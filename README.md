# Hyper Agent Markup Language (HAML) - README

## Overview
The Hyper Agent Markup Language (HAML) is designed to structure AI-driven conversations by defining agents, their interactions, and the overall flow of discussion. This language allows for dynamic and customizable conversations, perfect for simulations, debates, or collaborative discussions.

## Tags and Attributes

### 1. `<conversation>`
Defines the overall structure of the conversation, including the number of rounds, the topic, and the mood.

**Attributes:**
- `round`: (Required) The number of turns or exchanges in the conversation.
- `keyword`: (Optional) The main topic or focus of the conversation.
- `format`: (Optional) Specifies the format, such as "debate", "Q&A", "discussion", etc.
- `mood`: (Optional) The overall mood of the conversation, such as "serious", "humorous", etc.

**Example:**
```html
<conversation round="10" keyword="why people should go to Mars" format="debate" mood="serious">
```

### 2. `<agent>`
Defines each participant (agent) in the conversation, including their name, behavior, stake, and the model they will use.

**Attributes:**
- `name`: (Required) The name or identifier for the agent.
- `prompt`: (Required) A description of how the agent should behave or speak.
- `stake`: (Optional) The importance or influence of the agent in the conversation (e.g., 1 being less influential, 5 being most influential).
- `role`: (Optional) Specifies the agent’s role, such as "speaker", "respondent", "moderator", etc.
- `position`: (Optional) The agent’s stance on the topic, such as "for" or "against".
- `style`: (Optional) Defines the speaking style, e.g., "technical", "casual", "persuasive".

### 3. `<model>`
This tag is nested within the `<agent>` tag and defines the AI model that the agent will use to generate their part of the conversation.

**Attributes:**
- `name`: (Required) The name of the AI model (e.g., "GPT-4", "BERT", "CustomModelV2").
- `version`: (Optional) The version of the AI model.
- `parameters`: (Optional) Key parameters for the model, such as temperature, max tokens, etc.

**Example:**
```html
<agent name="elon" prompt="he talks like Elon Musk and wants to go to Mars" stake="1" role="speaker" position="for" style="visionary">
    <model name="gpt-4o" parameters="temperature=0.7;max_tokens=1500"/>
</agent>
```

### 4. `<interaction>`
Defines specific interactions between agents during the conversation, such as questions, challenges, or support.

**Attributes:**
- `type`: (Required) The type of interaction, such as "question", "challenge", "support".
- `from`: (Required) The name of the agent initiating the interaction.
- `to`: (Required) The name of the agent receiving the interaction.

**Example:**
```html
<interaction type="question" from="bill" to="elon"/>
```

### 5. `<context>`
Provides additional background or context for the conversation, such as setting, relevant data, or historical events.

**Attributes:**
- `time`: (Optional) Specifies the time period or setting (e.g., future, historical).
- `location`: (Optional) Specifies the location or setting (e.g., on Mars, UN conference, etc.).

**Example:**
```html
<context time="2030" location="UN Conference">
    <data source="NASA" type="report" url="https://nasa.gov/mars-colonization"/>
</context>
```

### 6. `<data>`
Embeds or references external data that agents can use to support their arguments.

**Attributes:**
- `source`: (Required) The origin of the data (e.g., "NASA", "World Bank").
- `type`: (Required) The type of data, such as "report", "study", "statistics".
- `url`: (Optional) The URL to the external data source.

**Example:**
```html
<data source="UN" type="policy" url="https://un.org/sustainable-development-goals"/>
```

### 7. `<decision>`
Defines a point in the conversation where agents must reach a decision or consensus.

**Attributes:**
- `method`: (Required) The method of decision-making, such as "vote", "consensus", "random".
- `outcome`: (Optional) Specifies the desired outcome or goal.

**Example:**
```html
<decision method="vote" outcome="should humanity prioritize Mars or Earth?"/>
```

### 8. `<summary>`
Concludes the conversation with a summary or final thoughts from the agents.

**Attributes:**
- `length`: (Optional) Specifies how detailed the summary should be (e.g., "brief", "detailed").

**Example:**
```html
<summary length="detailed"/>
```

## Example Usage

```html
<conversation round="10" keyword="why people should go to Mars" format="debate" mood="serious">
    
    <agent name="elon" prompt="he talks like Elon Musk and wants to go to Mars" stake="1" role="speaker" position="for" style="visionary">
        <model name="GPT-4" version="4.0" parameters="temperature=0.7;max_tokens=1500"/>
        <fund source="SpaceX" amount="1000000000" type="erc20" recipient="0xElonRecipientAddress" contract="0xSpaceXContractAddress" purpose="Mars colonization efforts"/>
        <advertisement company="Tesla" message="Drive the future with Tesla, the sustainable car for a sustainable planet." type="erc20" recipient="0xTeslaRecipientAddress" contract="0xTeslaContractAddress"/>
        <stake text="Stake on Elon" type="erc20" recipient="0xElonStakeAddress" contract="0xElonStakeContractAddress" />
    </agent>
    
    <agent name="bill" prompt="he talks like Bill Gates and wants to make Earth a better place" stake="2" role="respondent" position="against" style="pragmatic">
        <model name="GPT-4" version="4.0" parameters="temperature=0.5;max_tokens=1500"/>
        <fund source="Bill and Melinda Gates Foundation" amount="500000000" type="erc20" recipient="0xBillRecipientAddress" contract="0xGatesFoundationContractAddress" purpose="Global health and education"/>
        <advertisement company="Microsoft" message="Empowering the world with innovative technology solutions." type="erc20" recipient="0xMicrosoftRecipientAddress" contract="0xMicrosoftContractAddress"/>
        <stake text="Stake on Bill" type="erc20" recipient="0xBillStakeAddress" contract="0xBillStakeContractAddress" />
    </agent>
    
    <context time="2030" location="UN Conference">
        <data source="NASA" type="report" url="https://nasa.gov/mars-colonization"/>
        <data source="UN" type="policy" url="https://un.org/sustainable-development-goals"/>
    </context>

    <interaction type="question" from="bill" to="elon"/>
    <interaction type="challenge" from="elon" to="bill"/>

    <decision method="vote" outcome="should humanity prioritize Mars or Earth?"/>

    <summary length="detailed"/>
</conversation>
```

This example defines a structured debate between two agents, Elon and Bill, with interactions, contextual data, a decision-making process, and a detailed summary. Each agent uses a specified AI model to generate their contributions to the conversation.

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
```