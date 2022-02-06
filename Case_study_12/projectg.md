---
title: "Project"
author: "Lorenzo Leme"
date: "March 24, 2020"
output:
  html_document:  
    keep_md: true
    toc: true
    toc_float: true
    code_folding: hide
    fig_height: 6
    fig_width: 12
    fig_align: 'center'
---








```r
#maybe add DT
Juvlm <- lm
Juvlm <- lm(OT ~ G, data = Juv)
```


## Background

Soccer is the most watched sport in the world coming in with record breaking numbers in viewship. With lead strikers like Dybala, Cristiano Ronaldo, and Neymar getting paid upwards of $25 million a year plus sponsorships from major brands like Adidas and Emirates. Are these strikers worth the money and hype? With Dybala and Ronaldo both on the monster team, Juventus, I think that would be a great team to compare its statistics for. I want to look at both shots on target and the conversion of goals created to see how many shots on target it takes for a team to convert their shot into a goal.

Since we're trying to see if there's a direct relationship between the amount of shots on target taken and goals created our hypothesis will be stated as:

$$
  \underbrace{Y_i}_\text{Goals} = \overbrace{\beta_0}^\text{y-int} + \overbrace{\beta_1}^\text{slope} \underbrace{X_i}_\text{Shots on Targer} + \epsilon_i \quad \text{where} \ \epsilon_i \sim N(0, \sigma^2)
$$
Our null and alternative hypothesis will be written as such:
$$
H_0: \beta_1 = 0
$$
$$
 H_a: \beta_1 \neq 0
$$


```r
#plot(OT ~ G, xlab = "Goals", ylab = "On Target Attempts", main = "The Relationship Between Shots on Target and Goals Created", data = Juv)
#abline(Juvlm)
```


```r
ggplot(Juv, aes(x = G, y = OT))+
  geom_point()+
  geom_smooth(method = "lm")+
  labs(x="Goals", y="On Target Attempts", title = "Relationship Between Shots on Target and Goals Created")+
  theme_minimal()
```

![](projectg_files/figure-html/unnamed-chunk-5-1.png)<!-- -->


We can see that there is a direct relationship based on the plot displayed above. Simpily stated, as you commit to more shots that are near that goal, the higher the chance of you scoring is. Lets get more technical and look at our linear regression test.



```r
pander(summary(Juvlm))
```


---------------------------------------------------------------
     &nbsp;        Estimate   Std. Error   t value   Pr(>|t|)  
----------------- ---------- ------------ --------- -----------
 **(Intercept)**    7.971       1.333       5.98     5.106e-06 

      **G**         0.6671      0.3035      2.198     0.03875  
---------------------------------------------------------------


--------------------------------------------------------------
 Observations   Residual Std. Error   $R^2$    Adjusted $R^2$ 
-------------- --------------------- -------- ----------------
      24               2.556          0.1801       0.1428     
--------------------------------------------------------------

Table: Fitting linear model: OT ~ G

Looking at the regression test that we run, we can see that $p = 5.106e-06$. With a P-value that low we can determine that the slope is significant and that we have sufficient evidence to reject our null hypothesis. With ever shot attempt thats on target we increase the odds of scoring a goal by 0.6671. Lets check to see that our data is significant and constant enough to use below.


## Assumptions


```r
par(mfrow=c(1,3))

plot(Juvlm, which=1:2)

plot(Juvlm$residuals)
```

![](projectg_files/figure-html/unnamed-chunk-7-1.png)<!-- -->

According to the residuals vs fitted plot, we can see that our data doesn't really deviate from being considered normal. Our data is linear and has a constant variance according to our residuals plot. Our Q-Q plot is also on target and shows normality throughout our data. We finally look at our order plot to see if there are any trends that are apparent. Our order plot seems to be in check and shows no trends throughout the data. Our assumptions are correct and our data is viable and good to use.

## Interpretation

According to our data, the more shots on target that are produced, increases the chance that one will be a goal creation. On the otherhand, soccer is a hard sport to predict, it's unpredictable, but you can have great odds of something happening. The reason for its unpredictability is that it's a game made up of humans, these humans produce human errors. Goals aren't only dependent on the shot target accuracy but also power, stamina, weak foot, human block, and injuries that havent surfaced yet. This is why betting in soccer, and really any sport, can be difficult and dangerous because of how unpredictable it is. For example, during the round of 16 champions leage, FC Schlake scored two early goals against Man City. This was a team that's very low ranking, against the opposition in every way, almost out scoring their opponent. We did see a positive and meaningful relationship of the shot attempts, which is accurate, because the more you shot the more likely one's going to go in.
