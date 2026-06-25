On any given day, you’ll make thousands of decisions. Most of them don’t matter. So much so that the vast majority of our daily choices are silent. On a Monday, you might drive to work, drift through meetings, and enjoy a delicious turkey sandwich. Habits are critical to freeing up valuable cognitive processing power for essential tasks. But routine deludes us into believing that these choices are forks in the road, a single discrete decision set in stone. Instead, these decisions are continuous choices that reinforce the current course of action.

Next Monday, you could quit your job, sell your car, and become vegan. It may seem trivial, but this fallacy is at the heart of our misevaluation of risk. Inaction becomes the default, a “safe” option. Humans are horrendously bad at probabilistic thinking. Look no further than Daniel Kahneman's _Thinking Fast and Slow_ for abundant examples of how our brain's shortcuts undermine our ability to make rational decisions. Kahneman’s puzzles and experiments provide perfect information to their subjects, yet irrational choices are abundant. The worst mistake is assuming that inaction is the “safe” choice. Our default setting is cowardice.

## Gambling

To illustrate some fundamental aspects of risk evaluation, let’s flip a coin. Heads — you owe me $10, tails — I give you $5. It’s a bad bet. Hardcore gamblers might be inclined to play once, but nobody would take these chances in the long run.

Parameter Definition

Probability of winning

Probability of losing

Return if game is won

Cost of playing the game

The number of times we play the game

What if the payout, $r$, was $15? Assuming the coin is fair, rational actors should take the gamble. This is rule number one of decision making — take the action with the highest expected return.

$$ E(x) = pr+qc $$

If $E(x)$ is positive the statistician would advise you to take the gamble every time. Theory says the more often the bet is offered to you, the better your returns over time.

Assume we increase the stakes a thousand-fold. A 50% chance to win $15,000 for only $10,000. Statistically the expected returns are better than ever, but the proportion of people willing to play the game drops dramatically. Risk aversion scales with the stakes. The higher the stakes, the more risk averse people are. This is why you buy insurance for your home, car, and health but not your water-bottle or bed frame.

![utility.svg](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/5c35afe1-f3a7-405a-8655-70d84dac95f8/utility.svg)

This key to understanding this risk aversion is diminishing marginal utility. For any good, including money, the more we have the less we value it. A salary increase from $25,000 to $55,000 will provide more utility than one from $85,000 to $115,000. These increases are equivalent, but we would value them very differently.

For the same reason, losing $10,000 on a salary of $25,000 will bring far more disutility than losing $10,000 on a salary of $85,000. This piece of economics helps update our first rule — choose the action with the highest expected utility.

$$ E[U(x)] = p_U(r)+q_U(c) $$

Through this frame every decision we make brings us the most utility. This view of the world can only exist in one place — the dark, damp, and slightly spooky brain of an economist. The closest most of us get to optimal decision-making is the occasional pro-con list. We should give ourselves a break though, the story is about to get far more complicated.

## Risk is a Privilege






The graph above shows repeated coin flips games with good and bad odds. The dotted lines are the expected loss or gain after $n$ games played. Some of the trials follow their expected returns quite closely, but others deviate wildly. This variance is the second element of decision making — risk.

Risk means you can lose with a winning plan, or win with a losing one. The friend with a terrible workout routine and poor diet might end up with a perfect physique. More common is the inverse — the best laid plans of mice and men. Evaluating risk is difficult even when it’s known precisely.

Furthermore, luck means risk-taking is a privileged endeavor. Statistically sound economic opportunities can be out of reach for many who can’t afford the worst-case scenario. Venture capitalists can bet millions on up-and-coming startups, but the average American simply can’t afford the risk. Quitting a bad job is easier when homelessness isn’t a possibility.

![sad_histogram.svg](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/990dd44e-9d78-449f-92b7-6dca8fbc7521/sad_histogram.svg)

Even with favorable coin tosses, some people end up losing out. This scares me. Replacing coin tosses with large life decisions paints a terrifying scene. Some portion of the population will make the best decision with the given information and come out worse. A smaller portion will make 10 good decisions and come away with a lifetime of failure.

Fortunately, the world of statisticians and economists is built on a faulty premise — the past is indicative of the future. Unfortunately, this makes decision-making a terrifying prospect.

## Fuzzy Coins, Infinite Risk, & Opinions

The real world doesn’t offer perfect information. Would you take the coin flips if the odds and payoffs were murky? What if they were constantly changing? These “fuzzy” coins have probabilities of success that themselves are uncertain. These probabilities themselves have distributions.

![fuzzy_coins.svg](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/15514e63-78d5-40aa-8668-e908f6b52e02/fuzzy_coins.svg)