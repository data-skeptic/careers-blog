The past year has shown continued acceleration of the impact and reach of machine learning and artificial intelligence.  This was the year that diffusion model went mainstream with the release of tools like Dall-E, Midjourney, and Stable Diffusion.  Without a doubt, visual media has changed forever.  And while language models have been around for a while, the last year saw a lot more "last mile" problems solved, making tools like BERT and GPT-3 more accessible to non-developers.

There are many that raise concerns about joblessness in the wake of AI.  Yet what history is shown is that AI is more of a job creator than a job destroyer.  However, it is nearly certain that the landscape of jobs is going to change.  This can raise many questions for a professional looking to break into working in AI.

How can someone get their career in artificial intelligence moved forward?  I have 3 quick tips to share.

First and foremost, identify the role you want and a path to getting it.  Working in AI doesn't necessarily mean becoming a deep learning expert.  That is certainly one path forward, and an important team member to have in a large organization.  Advancements in AI require the aid of more than just researchers and ML engineers.  Product managers who understand the AI space can be instrumental in bringing new solutions to market.  Project managers that understand the difference between the software development lifecycle and the machine learning lifecycle are rare and valuable contriutors.

Second, understand the technology as deeply as you can.  Success as a front-end engineer building interfaces to ML models does not require that you've read the "Attention is all You Need" paper.  However, you should know something about transformer architecture in the same way a pilot understand a plane without being certified to make major repairs on it.  While the field can be intellectually intimidating, the concepts remain accessible with only a basic understanding of statistics and programming.  There's no shortage of learning resources.

Third, start to develop informed instincts about where AI can and cannot make an impact.  If you're working in this industry, you're going to hear a lot of elevator pitches to use AI in a new industry or new way.  AI is no magic.  There are some problems which are solvable with current state of the art approaches.  There are other problems that remain elusive.

Andrew Ng is often quoted for his "1 second rule" which states that if a trained human observer can answer a question in one second, then it should be possible to get a machine learning algorithm to learn how to answer the question.  Is there a cat in this photo?  Is this advertisement for a car company?  This rule, though crude, is surprisingly useful!

As I write this in the end of 2022, no serious professional in the AI field believes we are close to artificial general intelligence (AGI).  Still, many believe it may be possible without their lifetime.  There are many challenges, milestones, and steps along the way.  It's unclear if we yet have all the tools and technology we need, but there remains good reasons to believe we only need to scale our current efforts up.

Demand for every type of professional working with AI will continue to grow.  There will be more demand for researchers, R&D, ML Ops, etc.  Perhaps the largest area of job creation will be in the "go to market" roles that will be added to support efforts to leverage recent advancements.  Dozens or hundreds of companies will be started in the next few years attempting to take core underlying technologies like Stable Diffusion and bring it to market as a product a typical consumer can use.  Anyone can type a prompt into a box and see an image come up.  Not many people can make those images consistently interesting and print them on one-of-a-kind t-shirts.

The majority of these future companies will likely leverage open source image models like [Stable Diffusion](https://huggingface.co/spaces/stabilityai/stable-diffusion) or solutions like OpenAI's API (as seen used below).  The software that makes these tools accessible is already mature.  There are no technological limits why an ambitious entrepreneur couldn't immediately start building a business on top these tools.  So many will try.

```
import os
import openai

openai.api_key = 'sk-dsdsdsdsdsdsdsdsdsdsdsdsdsdsdsdsdsdsdsdsdsdsdsds'

prompt = '''This is the first sentence of a paragraph that Open AI will complete.'''

response = openai.Completion.create(
  model="text-davinci-002",
  prompt=prompt,
  temperature=0.7,
  max_tokens=60,
  top_p=1.0,
  frequency_penalty=0.0,
  presence_penalty=0.0
)

print(response.choices[0]['text'])
```

If you're serious about a career in AI, there's never been a better time to have an interest in the field.  There is no "winter" coming.  Even a full stop on all research advancements would leave years if not decades of useful work to be done helping small, medium, and large enterprise companies improve all aspects of their products and services through adoption of these powerful, yet sometimes narrowly useful tools.



