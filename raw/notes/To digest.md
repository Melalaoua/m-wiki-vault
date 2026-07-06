
https://walkinglabs.github.io/learn-harness-engineering/en/lectures/lecture-01-why-capable-agents-still-fail/
https://openai.com/index/harness-engineering/
https://ghuntley.com/loop/?action=signup&errorCode=TOKEN_EXPIRED&success=false




### Current function
  Labtests results, foreach pathology, have specific parameters that strengthen or weaken the probability of the patient having this disease, depending on the result. When a result is entered (currently binary negative/positive), the parameter is read in
  @src/assets/data/pathologies.json (do NOT read this file or just a subset as it is
  thousand lines long, here is a snippet below of what you can find in it)

  #### Pathologies.json
  Snippet content
  ```json
  "acute_pyelonephritis" : {
      "key": "acute_pyelonephritis",
      "symptoms": {...},
      "priors": {...},
      [Pasted text #1 +39 lines]
  ```

  Depending on the labtests result, foreach disease, a product is calculated in
  @src/core/dEngine/ through the @src/core/dEngine/pathologyPPost.ts .

  For now only binary result are allowed.

  #### Refactor proposed
  Some tests are more precise with numerical values. Thus a migration to handle numerical
  value, while keeping binary negative/positive actual system for some tests.

  The inbound pathologies.json will propose the this Json structure going forward when the dEngine is properly migrated :

```json
 "acute_pyelonephritis": {
		"key": "",
		"symptoms" : {...},
		"priors" : {...},
		"labtests": {	
			"test_crp": {
				"key": "test_crp",
				thresholds: {
					"crp_0_10" : {
						"key" : "crp_0_10",
						value_min: 0,
						value_max: 10,
						lr: 0.8
					},
					"crp_10_50" : {
						"key" : "crp_10_50",
						"value_min" : 10,
						"value_max" : 50,
						"lr" : 1.1
					},
					"crp_ge50": {
						"key" : "crp_ge50",
						"value_min" : 50,
						"value_max" : 9999,
						"lr" : 1.5
					}
				}
			},
			"test_rdt_malaria": {
				"key": "test_rdt_malaria",
				thresholds : {
					"pos" : {
						"key" : "pos",
						"lr" : 0.3
					},
					"neg" : {
						"key" : "neg",
						"lr" : 1
					}
				}
			}
		},
			"combined_labtests": {
				"combined_crp_rdt_malaria": {
					"key": "combined_crp_rdt_malaria",
					"test_a_key": "test_crp",
					"threshold_a_key": "crp_ge50",
					"value_a_min": 50,
					"value_b_max" : 9999,
					"test_b_key" : "test_rdt_malaria",
					"threshold_b_key" : "neg",
					"lr_pair": 1.5
				},
			///Second example with two numerical tests combined, cited tests are not in this current disease, just for sake of example
			"combined_": {
					"key": "combined_crp_rdt_malaria",
					"test_a_key": "test_crp",
					"threshold_a_key": "crp_ge50",
					"value_a_min": 50,
					"value_b_max" : 9999,
					"test_b_key" : "test_numerical_2",
					"threshold_b_key" : "numerical_10_30",
					"value_a_min": 10,
					"value_b_max" : 30,
					"lr_pair": 1.5
				},
}
```

Lower value is inclusive (equal and superior), max value is exclusive (strict less).

