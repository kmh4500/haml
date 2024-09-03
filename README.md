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

### 2. `<article>`
Defines the overall structure of the article, including the type of article, the main topic, and the tone.

**Attributes:**
- `type`: (Required) The type of article, such as "blog", "news", "editorial", "review", etc.
- `keyword`: (Optional) The main topic or focus of the article.
- `format`: (Optional) Specifies the structure or format of the article, such as "listicle", "opinion", "how-to", etc.
- `tone`: (Optional) The overall tone of the article, such as "informative", "persuasive", "casual", "formal", etc.

**Example:**
```html
<article type="blog" keyword="the benefits of space exploration" format="opinion" tone="informative">
```

### Attribute Details:

- **`type`**: 
  - This attribute specifies the category of the article.
  - Examples: "blog", "news", "editorial", "review", "feature", "how-to".

- **`keyword`**: 
  - This optional attribute defines the main subject or theme of the article. It helps focus the content on a specific topic.
  - Example: "renewable energy", "AI in healthcare", "latest smartphone trends".

- **`format`**: 
  - This optional attribute describes the structure of the article, indicating how the content is presented.
  - Examples:
    - "listicle": A list-based article format (e.g., "10 Reasons to Visit Mars").
    - "opinion": An article expressing a personal viewpoint.
    - "how-to": Step-by-step guides or instructional articles.
    - "review": A critical evaluation of a product, service, or experience.

- **`tone`**: 
  - This optional attribute sets the tone of the article, indicating the writer's style and approach.
  - Examples: 
    - "informative": Provides factual and clear information.
    - "persuasive": Aims to convince the reader of a particular viewpoint.
    - "casual": A relaxed and informal style.
    - "formal": A professional and serious approach.

### Example Usage Scenarios:

1. **Blog Post**:
   ```html
   <article type="blog" keyword="sustainable living tips" format="listicle" tone="casual">
   ```

2. **News Article**:
   ```html
   <article type="news" keyword="latest space exploration missions" format="feature" tone="informative">
   ```

3. **Editorial**:
   ```html
   <article type="editorial" keyword="the impact of AI on jobs" format="opinion" tone="persuasive">
   ```

### Summary:
The `<article>` tag provides a flexible framework for generating various types of written content, from casual blog posts to formal news articles. By adjusting the attributes, you can tailor the structure, focus, and tone of the content to suit different audiences and purposes.

### 3. `<agent>`
Defines each participant (agent) in the conversation, including their name, behavior, stake, and the model they will use.

**Attributes:**
- `name`: (Required) The name or identifier for the agent.
- `prompt`: (Required) A description of how the agent should behave or speak.
- `stake`: (Optional) The importance or influence of the agent in the conversation (e.g., 1 being less influential, 5 being most influential).
- `role`: (Optional) Specifies the agent’s role, such as "speaker", "respondent", "moderator", etc.
- `position`: (Optional) The agent’s stance on the topic, such as "for" or "against".
- `style`: (Optional) Defines the speaking style, e.g., "technical", "casual", "persuasive".

**Example:**
```html
<agent name="elon" prompt="he talks like Elon Musk and wants to go to Mars" stake="1" role="speaker" position="for" style="visionary">
    <model name="GPT-4" version="4.0" parameters="temperature=0.7;max_tokens=1500"/>
</agent>
```

### 4. `<model>`
This tag is nested within the `<agent>` tag and defines the AI model that the agent will use to generate their part of the conversation or image. The `<model>` tag can be used for both text-based AI models like GPT-4 and image generation models like Stable Diffusion.

**Attributes:**
- `name`: (Required) The name of the AI model (e.g., "GPT-4", "stable-diffusion-3-medium", "CustomModelV2").
- `version`: (Optional) The version of the AI model.
- `parameters`: (Optional) Key parameters for the model, such as temperature, max tokens, sampling steps, guidance scale, etc.

### Text-Based Models:
For text-based AI models like GPT-4, the parameters control how the model generates text. Typical parameters include:

- **`temperature`**: Controls the randomness of the output. A higher value (e.g., 1.0) makes the output more random, while a lower value (e.g., 0.2) makes it more deterministic.
- **`max_tokens`**: Limits the number of tokens (words or parts of words) in the generated output.
- **`top_p`**: Controls diversity via nucleus sampling; 0.9 means 90% of the probability mass.
- **`frequency_penalty`**: Discourages repetition in the text output.

**Example for Text-Based Model:**
```html
<agent name="elon" prompt="he talks like Elon Musk and wants to go to Mars" stake="1" role="speaker" position="for" style="visionary">
    <model name="GPT-4" version="4.0" parameters="temperature=0.7;max_tokens=1500"/>
</agent>
```

### Image-Based Models:
For image generation models like `stable-diffusion-3-medium`, the parameters define how the image is generated. Common parameters include:

- **`sampling_steps`**: The number of steps the model takes to generate the image. More steps typically improve quality but increase generation time.
- **`guidance_scale`**: Controls how closely the image should follow the prompt. Higher values make the image more literal to the description.
- **`seed`**: A random value that can be set to ensure the image is reproducible.

**Example for Image-Based Model:**
```html
<agent name="elon" prompt="he wants to visualize the Martian landscape with futuristic colonies" stake="1" role="artist" position="for" style="futuristic">
    <model name="stable-diffusion-3-medium" version="1.5" parameters="sampling_steps=50;guidance_scale=7.5;seed=42"/>
</agent>
```

### Summary:
- **Text Models (e.g., GPT-4)**: Focus on parameters like `temperature`, `max_tokens`, and `top_p` to control the style and content of the text output.
- **Image Models (e.g., stable-diffusion-3-medium)**: Use parameters like `sampling_steps`, `guidance_scale`, and `seed` to fine-tune the visual output.

These tags and parameters allow you to tailor the AI agent's behavior, whether generating text or images, according to your specific needs.
### 5. `<advertisement>`
Defines an advertisement within an agent's conversation turn. The advertisement can be associated with various payment models and is linked to a blockchain smart contract for transactions. It also supports integration with traditional ad networks like AdSense.

**Attributes:**
- `company`: (Required) The name of the company placing the advertisement.
- `message`: (Required) The message or slogan of the advertisement.
- `type`: (Required) The type of cryptocurrency or token used, such as "erc20". For AdSense, this can be left as "adsense".
- `recipient`: (Required) The blockchain address where payments or interactions will be sent. For AdSense, this can be an account identifier.
- `contract`: (Required) The smart contract address associated with the advertisement. Not required for AdSense.
- `cpc`: (Optional) The cost-per-click amount that the advertiser will pay for each click.
- `cpa`: (Optional) Cost-per-acquisition, where the advertiser pays for each specified action, such as a sale or sign-up.
- `cpm`: (Optional) Cost-per-mille, where the advertiser pays for every thousand impressions of the advertisement.
- `flatFee`: (Optional) A fixed fee that the advertiser pays for running the advertisement, regardless of clicks, impressions, or actions.
- `duration`: (Optional) The time period during which the advertisement will be active.
- `clickTrackingUrl`: (Optional) The URL used to track clicks for the advertisement.
- `actionTrackingUrl`: (Optional) The URL used to track specific actions (for CPA model) for the advertisement.
- `adsenseClientId`: (Optional) The AdSense client ID associated with the account.
- `adsenseAdSlot`: (Optional) The AdSense ad slot ID for the specific ad unit.

**Example for Blockchain-Based Advertisement:**
```html
<advertisement company="Tesla" message="Drive the future with Tesla, the sustainable car for a sustainable planet." type="erc20" recipient="0xTeslaRecipientAddress" contract="0xTeslaContractAddress" cpc="0.01" cpa="0.50" cpm="5.00" flatFee="100" duration="7d" clickTrackingUrl="https://example.com/track-click?ad_id=tesla1" actionTrackingUrl="https://example.com/track-action?ad_id=tesla1" />
```

**Example for AdSense Advertisement:**
```html
<advertisement company="Google" message="Discover the latest trends with Google." type="adsense" recipient="pub-1234567890" adsenseClientId="ca-pub-1234567890" adsenseAdSlot="1234567890" duration="30d" />
```

### Attribute Details:

- **`type`** (Required):
  - For blockchain-based ads, this would be the cryptocurrency or token type (e.g., "erc20").
  - For AdSense, this should be set to "adsense".

- **`adsenseClientId`** (Optional for AdSense):
  - The AdSense client ID associated with the account.
  - Example: `adsenseClientId="ca-pub-1234567890"`.

- **`adsenseAdSlot`** (Optional for AdSense):
  - The specific ad slot ID for the AdSense ad unit.
  - Example: `adsenseAdSlot="1234567890"`.

### 6. `<stake>`
Defines a staking mechanism within the conversation where users can stake cryptocurrency on a particular agent. This can be used to express support or confidence in the agent’s position.

**Attributes:**
- `text`: (Required) The label or call to action for the staking opportunity.
- `type`: (Required) The type of cryptocurrency or token used, such as "erc20".
- `recipient`: (Required) The blockchain address where the stakes will be sent.
- `contract`: (Required) The smart contract address associated with the staking mechanism.

**Example:**
```html
<stake text="Stake on Elon" type="erc20" recipient="0xElonStakeAddress" contract="0xElonStakeContractAddress" />
```

### 7. `<interaction>`
Defines specific interactions between agents during the conversation, such as questions, challenges, or support.

**Attributes:**
- `type`: (Required) The type of interaction, such as "question", "challenge", "support".
- `from`: (Required) The name of the agent initiating the interaction.
- `to`: (Required) The name of the agent receiving the interaction.

**Example:**
```html
<interaction type="question" from="bill" to="elon"/>
```

### 8. `<context>`
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

### 9. `<data>`
Embeds or references external data that agents can use to support their arguments.

**Attributes:**
- `source`: (Required) The origin of the data (e.g., "NASA", "World Bank").
- `type`: (Required) The type of data, such as "report", "study", "statistics".
- `url`: (Optional) The URL to the external data source.

**Example:**
```html
<data source="UN" type="policy" url="https://un.org/sustainable-development-goals"/>
```

### 10. `<decision>`
Defines a point in the conversation where agents must reach a decision or consensus.

**Attributes:**
- `method`: (Required) The method of decision-making, such as "vote", "consensus", "random".
- `outcome`: (Optional) Specifies the desired outcome or goal.

**Example:**
```html
<decision method="vote" outcome="should humanity prioritize Mars or Earth?"/>
```

### 11. `<summary>`
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
        <advertisement company="Tesla" message="Drive the future with Tesla, the sustainable car for a sustainable planet." type="erc20" recipient="0xTeslaRecipientAddress" contract="0xTeslaContractAddress" cpc="0.01" clickTrackingUrl="https://example.com/track-click?ad_id=tesla1" />
        <stake text="Stake on Elon" type="erc20" recipient="0xElonStakeAddress" contract="0xElonStakeContractAddress" />
    </agent>
    
    <agent name="bill" prompt="he talks like Bill Gates and wants to make Earth a better place" stake="2" role="respondent" position="against" style="pragmatic">
        <model name="GPT-4" version="4.0" parameters="temperature=0.5;max_tokens=1500"/>
        <advertisement company="Microsoft" message="Empowering the world with innovative technology solutions." type="erc20" recipient="0xMicrosoftRecipientAddress" contract="0xMicrosoftContractAddress" cpc="0.02" clickTrackingUrl="https://example.com/track-click?ad_id=microsoft1" />
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