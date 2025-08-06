# MCP Server: Background Job

MCP Server that enables coding agents to execute long-running shell commands asynchronously.

## Methods

Execute a command as background job, returns job id.
- `execute`: {command: `$command`} => {job_id: `$job_id`}

Inspect (tail) stdout/stderr, returns X number of lines.
- `tail`: {job_id: `$job_id`, lines: `$lines`} => {stdout: `$stdout`, stderr: `$stderr`}

Kill a background job.
- `kill`: {job_id: `$job_id`} => {status: `$status`}

List all background jobs.
- `list`: {} => {jobs: [{job_id: `$job_id`, status: `$status`, command: `$command`, started: `$utc`}] }

Get the status of a background job.
- `status`: {job_id: `$job_id`} => {status: `$status`}

Get the output of a background job.
- `output`: {job_id: `$job_id`} => {stdout: `$stdout`, stderr: `$stderr`}

Interact with a background job.
- `interact`: {job_id: `$job_id`, input: `$input`} => {stdout: `$stdout`, stderr: `$stderr`}

## Example Usage:

1. Claude Code or another terminal based coding agent has access to `mcp-background-job` server & can list tools
2. Agent uses `execute` tool with command `pnpm dev` and is returned with a `job_id`.
3. Agent can later inspect the job's status or output, interact with the process stdin, tail its log or kill it.
4. Agent can list all running tasks including the current status, original command & timestamp.
