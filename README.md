# Mattermost Steps

These steps allow you to call various APIs in Mattermost.

Steps included in this workflow:
- Create Channel
- Delete Channel
- Post to Channel
- Invite to Channel
- Get Channel Posts
- Beautify Posts

---------

<kbd>
<a href="https://support.xmatters.com/hc/en-us/community/topics">
   <img src="https://github.com/xmatters/xMatters-Labs/raw/master/media/disclaimer.png">
</a>
</kbd>

---------

# Files

* [MattermostSteps.zip](MattermostSteps.zip) - Workflow zip file with the step and example flow
* [mattermost.png](/mattermost.png) - Mattermost logo

# How it works
These steps use the [Mattermost API](https://api.mattermost.com/) to create channels, delete channels, post to channnels, invite to channels, and get conversations.


# Installation

## Mattermost Setup
These Mattermost steps use the [Personal Access Tokens](https://docs.mattermost.com/developer/personal-access-tokens.html) to authenticate. Follow their instructions at that link to generate one. This will be put in an xMatters constant.

Optionally install an xMatters agent on the Mattermost Server in order to communicate with Mattermost behind a firewall.

## xMatters Setup
1. Download the [MattermostSteps.zip](MattermostSteps.zip) file onto your local computer
2. Navigate to the Workflows tab of your xMatters instance
3. Click Import, and select the zip file you just downloaded
4. Add the Mattermost Personal Access Token to a constant in xMatters. Then use this constant in any **API Token** inputs on Mattermost steps in xMatters.


## Usage
The Mattermost steps are now available in your custom steps. So navigate to the appropriate canvas so you can add the step there. If you'd like to experiment with it, the **Steps** workflow has a canvas that can be triggered via HTTP call. 


## Create Channel

### Inputs
| Name  | Required? | Min | Max | Help Text | Default Value | Multiline |
| ----- | ----------| --- | --- | --------- | ------------- | --------- |
| API Token | Yes | 0 | 2000 | Personal Access Token from Mattermost | | No |
| Channel Name | Yes | 0 | 2000 | The UI Name for the channel to be created. If you would like the URL of this to be different, change the Channel Path parameter. | | No |
| Team | Yes | 0 | 2000 | Either the Team Name or the Team ID | | No |
| Type | Yes | 0 | 2000 | Whether the Channel is Public or Private. (public or o) and (private or p) are the valid inputs. | Public | No |
| Channel Path | No | 0 | 2000 | The name of the channel in the path. If left blank, this value will be the same as the channel name. | | No |
| Description | No | 0 | 2000 | Description for the channel. {purpose} | | No |
| Header | No | 0 | 2000 | Markdown-formatted text to display in the header of the channel | | No |


### Outputs

| Name | Description |
| ---- | ----------  |
| channel_id | Id of the newly created channel |
| json | JSON output from the API call |


## Delete Channel

### Inputs
| Name  | Required? | Min | Max | Help Text | Default Value | Multiline |
| ----- | ----------| --- | --- | --------- | ------------- | --------- |
| API Token | Yes | 0 | 2000 | Personal Access Token from Mattermost | | No |
| Channel Name | Yes | 0 | 2000 | The UI Name for the channel to be created. If you would like the URL of this to be different, change the Channel Path parameter. | | No |
| Team | Yes | 0 | 2000 | Either the Team Name or the Team ID | | No |


### Outputs

| Name | Description |
| ---- | ----------  |
| json | JSON output from the API call |


## Post to Channel

### Inputs
| Name  | Required? | Min | Max | Help Text | Default Value | Multiline |
| ----- | ----------| --- | --- | --------- | ------------- | --------- |
| API Token | Yes | 0 | 2000 | Personal Access Token from Mattermost | | No |
| Channel Name | Yes | 0 | 2000 | The UI Name for the channel to be created. If you would like the URL of this to be different, change the Channel Path parameter. | | No |
| Team | Yes | 0 | 2000 | Either the Team Name or the Team ID | | No |
| Message | Yes | 0 | 2000 | Content of the post | | No |

### Outputs

| Name | Description |
| ---- | ----------  |
| json | JSON output from the API call |


## Invite to Channel

### Inputs
| Name  | Required? | Min | Max | Help Text | Default Value | Multiline |
| ----- | ----------| --- | --- | --------- | ------------- | --------- |
| API Token | Yes | 0 | 2000 | Personal Access Token from Mattermost | | No |
| Channel Name | Yes | 0 | 2000 | The UI Name for the channel to be created. If you would like the URL of this to be different, change the Channel Path parameter. | | No |
| Team | Yes | 0 | 2000 | Either the Team Name or the Team ID | | No |
| User | Yes | 0 | 2000 | User to invite to channel. Either the user's Id, or username. | | No |


### Outputs

| Name | Description |
| ---- | ----------  |
| json | JSON output from the API call |

## Get Channel Posts

### Inputs
| Name  | Required? | Min | Max | Help Text | Default Value | Multiline |
| ----- | ----------| --- | --- | --------- | ------------- | --------- |
| API Token | Yes | 0 | 2000 | Personal Access Token from Mattermost | | No |
| Channel Name | Yes | 0 | 2000 | The UI Name for the channel to be created. If you would like the URL of this to be different, change the Channel Path parameter. | | No |
| Team | Yes | 0 | 2000 | Either the Team Name or the Team ID | | No |
| Max Messages | Yes | 0 | 2000 | The Max number of recent messages to return | 100 | No |


### Outputs

| Name | Description |
| ---- | ----------  |
| messages | Messages |
| replies | Replies to messages |
| error | Any error messages will be put here. |


## Beautify Posts

### Inputs
| Name  | Required? | Min | Max | Help Text | Default Value | Multiline |
| ----- | ----------| --- | --- | --------- | ------------- | --------- |
| API Token | Yes | 0 | 2000 | Personal Access Token from Mattermost | | No |
| Messages | Yes | 0 | 20000 | Messages from Get Channel Posts step | | No |
| Replies | Yes | 0 | 20000 | Replies from Get Channel Posts step. | | No |
| Timezone | Yes | 0 | 2000 | Timezone message timestamps should be in. Format like America/New_York. | America/New_York | No |
| Error | No | 0 | 2000 | Any errors that occurred in the Get Channel Posts Step. | | No |


### Outputs

| Name | Description |
| ---- | ----------  |
| posts | Posts formatted nicely |


## Example
This is an image of the provided flow in xMatters.

<kbd>
	<img src="/media/ExampleFlow.png">
</kbd>

