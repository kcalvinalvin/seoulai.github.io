---
layout: hackathon
title: SeoulAI Hackathon
date: Saturday, December 15, 2018 10:00:00 PM GMT+09:00
description: Seoul AI is hosting 4th AI hackathon on Saturday, December 15th. Hackathon is based on the new toolkit from Seoul AI Gym
tags:
  [
    Seoul,
    "Artificial Intelligence",
    meetup,
    AI,
    call,
    presenters,
    practioners,
    "Machine Learning",
    Korea,
    Gangnam,
    2017,
    2018,
    Hackathon,
  ]
---

{% capture event_info %}


# Overview

Seoul AI is hosting our 4th AI hackathon on **Saturday, 15th of December**. This hackathon is based on a new toolkit from SeoulAI for developing AI algorithms: Seoul AI Grm. This gym simulates various environments and enables the use of any teaching techniques on an agent. The goal of every hackathon participant is to develop an agent that can trade cryptocurrency. Each participant will train an agent to compete to become the most successful trader. Participants are free to chose any machine learning algorithm of their choice. SeoulAI will provide the dataset. The agent will be provided via REST API and train in real time.


# Competition
All agents will receive 100,000,000KRW at 10:00. The agent with the highest revenue by 18:50 will be the winner of the competition. 

We encourage you to participate in the competition from the start of the competition, but you can join at any time on December 15th. 


# Judging Criteria

- Revenue = (portfolio value /10,000,000 KRW) * 100 (%)
- Portfolio value = cash + balance amount * current value (at 18:50)
- Agents with a return lower than 0% will be disqualified.
- If there is a tie, the agent with the higher transaction number wins.


# Prizes

The winner will receive Apple AirPods.


# Important information

- The hackathon_id (agent_id) you enter on <a href="http://bit.ly/seoulai_market_hackathon"> Form </a> must be the same as your agent class.
- Order quantity, cash and balance will be calculated to the 4th decimal place.
-  
- 
- Buy order'll be concluded at the first sell price and Sell order'll be concluded at the first buy price. The probability of conclusion'll be 100%. (refer to technical information)
- Buy and sell order can be executed as the unit of available quantity in percent. (refer to technical information)
- The buy and sell commissions are 0.05%.
- If you have less than 1,000 KRW in cash, your order will automatically be changed to hold order (Minimum order amount is 1,000 KRW)
- If your balance is 0, and you place an order to sell, it will automatically be changed to hold order.
- There are no restrictions on trading methods. Reinforcement learning, rule based methods, direct trading and other methods are all possible.


# Schedule

Saturday, 15th of December, 2018

- 10:00 - 10:15 Opening
- 10:15 - 10:30 Introduction to Seoul AI Gym and the Market environment
- 10:30 - 12:30 Hacking
- 12:30 - 1:30 Lunch 
- 13:30 - 18:50 Hacking
- 18:50 - 19:00 Winner announcement 

# Registration

All participands must register their *hackathon_id* (agent_id) through this <a href="http://bit.ly/seoulai_market_hackathon">Form</a>

If you have any questions, feel free to ask us at seoul.ai.global@gmail.com


# Location

Hyperconnect
14th floor, Daegak Bldg., 
5, Seocho-daero 78-gil, 
Seocho-gu, Seoul, 
Republic of Korea

<iframe src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3165.4515690893822!2d127.02735559999999!3d37.4972664!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x357ca15a2f9719ab%3A0x20210a76b2b256f7!2z64yA6rCB67mM65Sp!5e0!3m2!1sen!2s!4v1508801167955" width="100%" height="450" frameborder="0" style="border:0" allowfullscreen=""></iframe>

# Venue

<div class="user-projects">
  <div class="images-left">
    <a href="{{ "/assets/img/hackathon/venue1.jpg" | prepend: site.baseurl }}" target="_blank">
    <img src="{{ "/assets/img/hackathon/venue1.jpg" | prepend: site.baseurl }}" />
    </a>
  </div>
  <div class="images-right">
    <a href="{{ "/assets/img/hackathon/venue2.jpg" | prepend: site.baseurl }}" target="_blank">
    <img src="{{ "/assets/img/hackathon/venue2.jpg" | prepend: site.baseurl }}" />
    </a>
  </div>
</div>
<div class="user-projects">
  <div class="images-left">
    <a href="{{ "/assets/img/hackathon/venue3.jpg" | prepend: site.baseurl }}" target="_blank">
    <img src="{{ "/assets/img/hackathon/venue3.jpg" | prepend: site.baseurl }}" />
    </a>
  </div>
  <div class="images-right">
    <a href="{{ "/assets/img/hackathon/venue4.jpg" | prepend: site.baseurl }}" target="_blank">
    <img src="{{ "/assets/img/hackathon/venue4.jpg" | prepend: site.baseurl }}" />
    </a>
  </div>
</div>

# Sponsors

<div class="user-projects" style="vertical-align: center">
  <div class="images-left">
    <img src="{{ "/assets/img/hackathon/hpcnt.png" | prepend: site.baseurl }}" />
  </div>
  <div class="images-right">
    <img src="{{ "/assets/img/hackathon/aws.png" | prepend: site.baseurl }}" />
  </div>
</div>

{% endcapture %}

{% capture technical_info %}

# Technical information

You can check our latest documentation on [GitHub](https://github.com/seoulai/gym/blob/master/seoulai_gym/e
nvs/market/README.md). If you encounter any issues, please create an issue on [GitHub Issues](https://github.com/seoulai/gym/issues) and we will try to take care of it as soon as possible.

You will need Python v 3.6 to run the Seoul AI Market environment.


## Installation

install from source.

```bash
git clone -b market https://github.com/seoulai/gym.git

cd gym

pip3 install -e .
```


## Seoul AI Market Framework

Seoul AI Market is based ona real-time <a href="https://github.com/seoulai/gym">reinforcement learning</a> based method.


{% highlight python %}

import seoulai_gym as gym
from itertools import count
from seoulai_gym.envs.market.base import Constants

your_id = "seoul_ai"
mode = Constants.LOCAL

# Create your agent.
a1 = YourAgentClassName(
     your_id,
     )

# Create your market environment. 
env = gym.make("Market")

# Select your id and mode to participate
env.participate(your_id, mode)

# reset fetches the initial state of the crypto market.
obs = env.reset()

# Perform real-time reinforcement learning
for t in count():
    # Call act for the agent to take an action
    action = a1.act(obs)
    
    # To send your action to market:  
    obs, rewards, done, _ = env.step(**action)
    
    # We reccomend that rewards override user-defined fuctions
    a1.postprocess(obs, action, next_obs, rewards)

{% endhighlight %}

## Setup details 

### mode

- There are 2 modes: LOCAL and HACKATHON.
- Your agent will start trading in HACKATHON mode. This will affect the virtual KRW balance provided by Seoul AI.
- You can trian your agent in the LOCAL mode. We advice you to train your agent before trying out the HACKATHON mode.

#### LOCAL mode Example 1

```python
your_id = "seoul_ai"
mode = Constants.LOCAL

env = gym.make("Market")
env.participate(your_id, mode)

# IF you call reset in LOCAL, your cash and balance will be updated to 100,000,000 KRW and 0.0 respectively.
obs = env.reset()

for t in count():
    action = a1.act(obs)
    next_obs, rewards, done, _ = env.step(**action)    # action is in dictionary format.
    a1.postprocess(obs, action, next_obs, rewards)
```

#### LOCAL mode Example 2

```python
your_id = "seoul_ai"
mode = Constants.LOCAL

env = gym.make("Market")
env.participate(your_id, mode)

obs = env.reset()

# You can use Episodes under LOCAL mode to train similar scenarios.
EPISODES = 100
for e in EPISODES: 
    for t in count():
        action = a1.act(obs)
        next_obs, rewards, done, _ = env.step(**action)    # action is in dictionary format.
        a1.postprocess(obs, action, next_obs, rewards)
    
        # The game ends once the agent has been trained on all Local data
        if done:
            break
```

#### HACKATHON mode Example

```python
your_id = "seoul_ai"
mode = Constants.HACKATHON

env = gym.make("Market")
env.participate(your_id, mode)

# Calling reset in HACKATHON mode fetches the cash and balance
# It is different from calling reset in LOCAL as your cash and balance will not be reset.
obs = env.reset()


# You cannot train with Episodes in HACKATHON mode.
for t in count():
    action = a1.act(obs)
    next_obs, rewards, done, _ = env.step(**action)    # action is in dictionary format.
    a1.postprocess(obs, action, next_obs, rewards)
```

### act

```python
action = a1.act(obs)
```
The act function calls the following functions.
- _get_common() = saves raw data fetched by obs to as an agent class variable
- preprocess() = changes raw data fetched by obs to state
- algo() = performs training as defined by the participant.

    
### step
The step function fetches and saves the crypto market state so that the agent may start trading. This function returns 3 variables.

#### `obs`
obs is short for observation.
The datasets in obs are as follows:

```python
order_book = obs.get("order_book")    # [Buy price, Current price, Sell price]
statistics = obs.get("statistics")    # {Statistical value for agent's use}
agent_info = obs.get("agent_info")    # {Cash, balance amount}
portfolio_rets = obs.get("portfolio_rets")    # {Portfolio indicators based on algorithm performance}
```
#### `rewards`
There are 5 types of rewards

```python
rewards = dict(
    return_amt=return_amt,    # Revenue from current action
    return_per=return_per,    # Yield from current action (current value of portfolio/ previous value of portfolio -1) * 100(%)
    return_sign=return_sign,    # 1 if profited from current action. -1 if loss. 0 if no change. 
    score_amt=score_amt,    # Amount of revenue (or profit or loss) incurred to date relative to initial capital (10,000,0000 KRW)
    score=score)    # Revenue (or profit or loss) incurred to date relative to initial capital (110,000,0000 KRW) (%)
```

#### `done`
The value of done is always False under HACKATHON mode.


### Developing Agent class

#### Creating your agent

```python
import seoulai_gym as gym
from seoulai_gym.envs.market.agents import Agent

# Your agent must inherit from Seoul AI's agent class
class YourAgentClassName(Agent):
    ...
```

#### _get_common() function
_get_common function calls agent's act function. obs takes raw data and saves it as a variable in the agent's class.
```python
    def _get_common(
        self,
        obs,
    ):
        self.order_book = obs.get("order_book")
        self.statistics = obs.get("statistics")

        self.agent_info = obs.get("agent_info")
        self.portfolio_ret = obs.get("portfolio_rets")

        self.cash = self.agent_info["cash"]
        self.asset_qtys = self.agent_info.get("asset_qtys")    # balance amount
        self.cur_price = self.order_book[0+1]    # current price
```

#### set_actions function defition
All participants must define the set_action function.
actions must be in dictionary form and must be returned.

```python
class YourAgentClassName(Agent):

    def set_actions(
        self,
    )->dict:

        your_actions = {}

        """ 
        The dictionary's key is action name, value is order_percent.
        action name is named by the participant
        order_percent takes value between -100 and 100
        order_percent values + represents to buy and - represents to sell.
       """

        your_actions = dict(
            holding = 0,
            buy_all = +100,    # buy_all means that you will buy 100% of the purchase amount
            sell_20per = -20,  # sell_20per means buy and sell 20% of the available volume
        )
        return your_actions    # You must return the actions dictionary you defined.
```

#### preprocess
You can select your data from raw data (fetched by obs), and change it as you'd like. We encourage that you perform data normalization.

- preprocess is optional. If omitted, obs is entered as state.

```python
    def preprocess(
        self,
        obs,
    ):
        cur_price = self.cur_price
        ma10 = self.statistics.get("ma10")
        std10 = self.statistics.get("std10")
        thresh_hold = 1.0

        your_state = dict(
            buy_signal=(cur_price > ma10 + std10*thresh_hold),
            sell_signal=(cur_price < ma10 - std10*thresh_hold),
        )

        return your_state
```

#### algo (algorithm definition)
It is a function that defines the conditions for tradtion.

```python
    def algo(
        self,
        state,
    ):
        if state["buy_signal"]:
            # Enter action_name as a parameter of set_actions
            return self.action("buy_all")
        elif state["sell_signal"]:
            return self.action("sell_20per")
        else:
            return self.action(0)    # You can enter the index of the action_name defined in set_actions as a parameter.
```

#### postprocess
You can redifine rewards through the postprocess.
```python
    def postprocess(
        self,
        obs,
        action,
        next_obs,
        rewards,
    ):
        your_reward = 0

        decision = action.get("decision")
        order_book = obs.get("order_book")
        cur_price = order_book[0+1]

        next_order_book = obs.get("order_book")
        next_price = next_order_book[0+1]
        diff = next_price - cur_price

        if decision == Constants.BUY and diff > 0:
            your_reward = 1
        elif decision == Constants.SELL and diff < 0:
            your_reward = 1
```

#### DQN Example
```python
# link 1
```

#### Rule based Example
```python
# link 2
```

{% endcapture %}

{% capture build_with %}

<footer class="footer">
    <p>Build with <span class="love">❤</span> by <a href="#" target="_blank">Imane</a></p>
</footer>
  
{% endcapture %}

{% include hackathon.html %}
