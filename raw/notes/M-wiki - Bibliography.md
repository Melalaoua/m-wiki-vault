This system is build based on [[Improve monitoring and bibliographic management]]. It is embedded in [[MeepsScribe]], both for my phd and personal brains.


You're doing great works. Let me add more speficiations to enhance your strategy. 

Workspace mastra doc:

A Mastra workspace gives agents a persistent environment for storing files and executing commands. Agents use workspace tools to read and write files, run shell commands, and search indexed content.

A workspace supports the following features:

- [Filesystem](https://mastra.ai/docs/workspace/filesystem): File storage (read, write, list, delete, copy, move, grep)
    
- [Sandbox](https://mastra.ai/docs/workspace/sandbox): Command execution (shell commands) and background processes
    
- [LSP inspection](https://mastra.ai/docs/workspace/lsp): Hover, definition, and implementation queries through language servers
    
- [Search](https://mastra.ai/docs/workspace/search): BM25, vector, or hybrid search over indexed content
    
- [Skills](https://mastra.ai/docs/workspace/skills): Reusable instructions for agents
    

When to use workspaces

Use a workspace when your agent needs access to the local filesystem, shell commands, semantic code inspection, indexed search, or reusable skill instructions.

How it works

When you assign a workspace to an agent, Mastra includes the corresponding tools in the agent's toolset. The agent can then use these tools to interact with files and execute commands.

You can create a workspace with any combination of the supported features. The agent receives only the tools relevant to what's configured.

Usage

Creating a workspace

Create a workspace by instantiating the `Workspace` class with your desired features:

src/mastra/workspaces.ts

```
import { Workspace, LocalFilesystem, LocalSandbox } from '@mastra/core/workspace'

const workspace = new Workspace({
  filesystem: new LocalFilesystem({
    basePath: './workspace',
  }),
  sandbox: new LocalSandbox({
    workingDirectory: './workspace',
  }),
  skills: ['skills'],
})
```

The `skills` array specifies paths to directories containing skill definitions, see [Skills](https://mastra.ai/docs/workspace/skills).

Global workspace

Set a workspace on the Mastra instance. All agents inherit this workspace unless they define their own:

src/mastra/index.ts

```
import { Mastra } from '@mastra/core'
import { Workspace, LocalFilesystem } from '@mastra/core/workspace'

const workspace = new Workspace({
  filesystem: new LocalFilesystem({ basePath: './workspace' }),
})

const mastra = new Mastra({
  workspace,
})
```

Agent-level workspace

Assign a workspace directly to an agent to override the global workspace:

src/mastra/agents/my-agent.ts

```
import { Agent } from '@mastra/core/agent'
import { Workspace, LocalFilesystem } from '@mastra/core/workspace'

const workspace = new Workspace({
  filesystem: new LocalFilesystem({ basePath: './agent-workspace' }),
})

export const myAgent = new Agent({
  id: 'my-agent',
  model: 'openai/gpt-5.5',
  workspace,
})
```

Configuration patterns

Workspaces support several configuration patterns depending on what capabilities your agent needs. The two main building blocks are `filesystem` (file tools) and `sandbox` (command execution), with `mounts` as the way to bridge cloud storage into sandboxes.

Filesystem + sandbox (local)

For local development, pair a `LocalFilesystem` and `LocalSandbox` pointed at the same directory. Since both operate on the local machine, files written through the filesystem are immediately available to commands in the sandbox:

```
const workspace = new Workspace({
  filesystem: new LocalFilesystem({ basePath: './workspace' }),
  sandbox: new LocalSandbox({ workingDirectory: './workspace' }),
})
```

The agent receives both file tools and `execute_command`. This is the simplest full-featured setup.

--------------------------------

### Initialize Workspace with Local Filesystem and Sandbox

Source: [https://github.com/mastra-ai/mastra/blob/main/docs/src/content/en/reference/workspace/workspace-class.mdx](https://github.com/mastra-ai/mastra/blob/main/docs/src/content/en/reference/workspace/workspace-class.mdx)

This snippet demonstrates how to create a new Workspace instance, configuring it with a LocalFilesystem for file storage and a LocalSandbox for command execution. It also enables BM25 search and specifies paths for automatic indexing.

```typescript

import { Workspace, LocalFilesystem, LocalSandbox } from '@mastra/core/workspace'

const workspace = new Workspace({

id: 'my-workspace',

name: 'My Workspace',

filesystem: new LocalFilesystem({

basePath: './workspace',

}),

sandbox: new LocalSandbox({

workingDirectory: './workspace',

}),

bm25: true,

autoIndexPaths: ['docs'],

})

The idea would be to have a mastra agent connecter to a discord adapter (discord bot). The mastra agent would invoke tools to execute the plan you are building