# Slack MCP Server

MCP Server for the Slack API, enabling Claude to interact with Slack workspaces.

## Tools

1. `slack_list_channels`
   - List public or pre-defined channels in the workspace
   - Optional inputs:
     - `limit` (number, default: 100, max: 200): Maximum number of channels to return
     - `cursor` (string): Pagination cursor for next page
   - Returns: List of channels with their IDs and information

2. `slack_post_message`
   - Post a new message to a Slack channel
   - Required inputs:
     - `channel_id` (string): The ID of the channel to post to
     - `text` (string): The message text to post
   - Returns: Message posting confirmation and timestamp

3. `slack_reply_to_thread`
   - Reply to a specific message thread
   - Required inputs:
     - `channel_id` (string): The channel containing the thread
     - `thread_ts` (string): Timestamp of the parent message
     - `text` (string): The reply text
   - Returns: Reply confirmation and timestamp

4. `slack_add_reaction`
   - Add an emoji reaction to a message
   - Required inputs:
     - `channel_id` (string): The channel containing the message
     - `timestamp` (string): Message timestamp to react to
     - `reaction` (string): Emoji name without colons
   - Returns: Reaction confirmation

5. `slack_get_channel_history`
   - Get recent messages from a channel
   - Required inputs:
     - `channel_id` (string): The channel ID
   - Optional inputs:
     - `limit` (number, default: 10): Number of messages to retrieve
   - Returns: List of messages with their content and metadata

6. `slack_get_thread_replies`
   - Get all replies in a message thread
   - Required inputs:
     - `channel_id` (string): The channel containing the thread
     - `thread_ts` (string): Timestamp of the parent message
   - Returns: List of replies with their content and metadata


7. `slack_get_users`
   - Get list of workspace users with basic profile information
   - Optional inputs:
     - `cursor` (string): Pagination cursor for next page
     - `limit` (number, default: 100, max: 200): Maximum users to return
   - Returns: List of users with their basic profiles

8. `slack_get_user_profile`
   - Get detailed profile information for a specific user
   - Required inputs:
     - `user_id` (string): The user's ID
   - Returns: Detailed user profile information

## Setup 

1. Create a Slack App.
2. Configure Bot Token Scopes:
3. Install App to Workspace:


### Environment Variables

1. `SLACK_BOT_TOKEN`: Required. The Bot User OAuth Token starting with `xoxb-`.
2. `SLACK_TEAM_ID`: Required. Your Slack workspace ID starting with `T`.
3. `SLACK_CHANNEL_IDS`: Optional. Comma-separated list of channel IDs to limit channel access (e.g., "C01234567, C76543210"). If not set, all public channels will be listed.

### Additional setup
Adding an HTTP server component to bot to handle Slack events directly and respond to messages in channels . Using Express.js, a popular and lightweight web framework for Node.js.

npm install express body-parser dotenv @slack/types
npm install @slack/events-api

