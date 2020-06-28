---
follows: dataShape.md
id: litvis
---

@import "../css/datavis.less"

# Undergraduate Coursework Template

{(questions|}

- What has been the change in the amount of cases globally
- What has been the change in the amount of cases in the world apart from China
- Compare the amount that have recovered and the amount that have died globally.

{|questions)}

{(visualization|}

```elm {l=hidden v}
confirmedBarchart : Spec
confirmedBarchart =
    let
        data =
            dataFromColumns []
                << dataColumn "Date" (strColumn "Date" dataset |> strs)
                << dataColumn "Confirmed" (numColumn "Confirmed" dataset |> nums)

        enc =
            encoding
                << position X [ pName "Date", pTemporal, pTitle "Date" ]
                << position Y [ pName "Confirmed", pQuant, pTitle "Confirmed" ]
    in
    toVegaLite
        [ height 300
        , width 400
        , data []
        , enc []
        , bar [ maColor "rgb(125,0,125)" ]
        ]
```

```elm {l=hidden v}
deathsBarchart : Spec
deathsBarchart =
    let
        data =
            dataFromColumns []
                << dataColumn "Date" (strColumn "Date" dataset |> strs)
                << dataColumn "Deaths" (numColumn "Deaths" dataset |> nums)

        enc =
            encoding
                << position X [ pName "Date", pTemporal, pTitle "Date" ]
                << position Y [ pName "Deaths", pQuant, pTitle "Deaths" ]
    in
    toVegaLite
        [ height 300
        , width 400
        , data []
        , enc []
        , bar [ maColor "rgb(255,0,0)" ]
        ]
```

```elm {l=hidden v}
recoveredBarchart : Spec
recoveredBarchart =
    let
        data =
            dataFromColumns []
                << dataColumn "Date" (strColumn "Date" dataset |> strs)
                << dataColumn "Recovered" (numColumn "Recovered" dataset |> nums)

        enc =
            encoding
                << position X [ pName "Date", pTemporal, pTitle "Date" ]
                << position Y [ pName "Recovered", pQuant, pTitle "Recovered" ]
    in
    toVegaLite
        [ height 300
        , width 400
        , data []
        , enc []
        , bar [ maColor "rgb(0,255,0)" ]
        ]
```

![graph1](graph.jpg "Barchart comparing confirmed cases to the data globally apart from China")
![graph2](graph2.jpg "Barchart of cases in China currently (as of 26th April 2020)")
![graph3](graph3.jpg "Comparing Deaths to Recovered Globally")

{|visualization)}

{(insights|}

**Overall Insights**

- As seen in all of the barcharts, there was an increase in the _myBarchart_ graph as time went which is understandable due to the fact it was only going to increase before it decreases as we have seen in China according to the [Our World in Data](https://ourworldindata.org/coronavirus) on the _'COVID-19 – Daily new confirmed deaths – rolling 3-day average'_ graph.
- However this heavily depends on whether Social Distancing is practiced or not. Below is a diagram based on this from the [Washington Post](https://www.washingtonpost.com/graphics/2020/world/corona-simulator/?mod=article_inline) where the blue (#AAC6CA) is people who are healthy, orange (#BB641D) is people who are infected and purple (#CB8AC0) is people who are recovered.
  ![Social Distancing practice](SocialDistancing.png "Practising social distancing")

**Research Insights**

1. Globally, there has been an increasing change, however it doesn't display in the dataset that I have chosen that there are several peaks globally (as well as within each country, more on that later) and eventually there will be a 'steady' decrease or halt to the number of confirmed cases as well as the number of deaths overall. As far as this graph has shown, there will only be an increase (and potentially second peak according to the news recently) before there is a decrease in the amount of cases globally. This makes sense as far as social distancing and a lockdown is considered as it allows for the virus to be spread less as well as ensure that people are doing everything they can to ensure the virus doesn't spread.
   As you can see in the [Worldometer 'Daily New Cases' graph](https://www.worldometers.info/coronavirus/coronavirus-cases/) the statistics prove that there will a fluctuation in the amount of cases that there are worldwide from 27th March 2020 onwards. This is likely due to people not following govrenment rules. However as seen by China on the [Worldometer 'Daily New Cases' graph](https://www.worldometers.info/coronavirus/country/china/) there will be a smaller peak first before a massive peak and only then will numbers be reduced drastically. As well as this on the same page, you can see that there is a slope in the amount of cases that are in China.
2. You can mostly see overall that there is an increase globally aside from China. However based on China's stats there hasn't been an increase or decrease recently as per the [Our World in Data](https://ourworldindata.org/coronavirus) website.
   So therefore comparing world statistics to that of China's (that has almost completely recovered from the virus or at least has a reduced number of cases) as well as comparing it to the bar charts, I can safely say that the increase is understandable.
   There will be a lot of deaths just like it had occurred in China, however there will be a lot more recoveries as shown in the barchart as well (though those statistics are based on overall cases in other countries as well)
3. Overall, it is obvious that there have been a lot of deaths but there have been a lot more recoveries in all countries than deaths. This is unfortunately not what the world often sees as people and the government are understandably more concerned in tackling how to reduce the virus than to see the numbers rising every day. There will be an increase in confirmed cases and there will be a rise in the amount of deaths that occur due to the virus, however there are a lot more recovered cases than deaths and this is mostly due to the fact that nearly everyone has followed government rules and guidelines in order to ensure that people are less likely to give the virus to anyone else.
   Based on looking over the dataset that I have chosen as well as in the scatter graphs, it is obvious that there are a lot more cases in China/Mainland China than there are in the rest of the world and that is mostly due to the fact that the virus in a way originated in Wuhan, China due to a pneumonia of an unknown cause.

{|insights)}

{(designJustification|}

- The barcharts that were not drawn were for the basic understanding of the data that was in the dataset. However, they do give an insight into mostly all of the research questions.
- Each barchart has a colour as it allows for each barchart to be understood correctly without having to look at the axis. Red is associated with death, green is associated with recovering and purple is the neutral colour (for those that have been confirmed with coronavirus)
- While comparing the barcharts to each other it is very obvious to see how the data is comparable, or not-so-comparable, as it allows you to see that there is an increase no matter what.
- The bar graphs that I had drawn were created in order to ensure that I was able to compare all of available data that I wanted to compare overall. Adding bar labels to these graphs were necessary as it allowed people to realise what exactly is being compared. It also shows the increase in each country individually so therefore it is useful for answering specific questions while also comparing one column to itself. Although this was not initially going to be part of the visualisations, I had decided to keep those graphs in so that the flow of the way the graphs are displayed.
- Where the third research question are much more specific compared to the first two research questions, the barcharts help with the basic understanding of the first two research questions and the scatter graphs help with more complex discussions about the questions. It is very useful for complex questions to be answered with complex answers and with complex justifications so that it can be appropriately backed up with the correct information.
- Having had research questions that are more about comparing the data, the bar charts were provided in order to view the comparisons in deaths, recovered and confirmed cases worldwide in order of the date.
- The colour schemes of the bar charts that I had drawn were going to be based on the bar charts that I had initially created in order to make sure that even when not looking at the axis, someone was able to tell which section was for what such as red for deaths and green for recovered.
- Although the dataset that I had used was last updated on 4th February 2020, it doesn't show that there will be a decrease in numbers or whether there will be a second peak or not. However due to looking at the news as well as look at several websites that are linked below in the references as well as through out this coursework as it had assisted me with more up-to-date information to help me answer with most if not all my research questions.
- I was going to do scatter graphs so that each country could be visible however there were too many countries to add so therefore there would have been too many colours so therefore resulted in the graphs not being user friendly and wouldnt have been useful for those that are colour blind or visually impaired.
- Originally I was planning on creating a spacial graph based on those that have died, recovered and have been confirmed, however I didn't have the means to do that due to the fact that I did not have longitude and latitude values to each of the cities and countries and some of the values may not be accurate if seaerched for. As well as this, some of the _Sno_ ids don't have a city or state that the cases were in so therefore it was not any use to use spacial data. I think this design would have been useful however as it would have allowed me to view each countries statistics clearly and more visually instead of through a barchart or a scatter graph. As well as this, it would have been better for those that are visually impaired or colour blind as there would only be 3 colours (those that are recovered, those that are confirmed with coronavirus and those that are dead) rather than 32 different colours for 32 different countries.

{|designJustification)}

{(references|}

https://geojson-maps.ash.ms/ (1/4/2020)
https://informationisbeautiful.net/visualizations/covid-19-coronavirus-infographic-datapack/ (2/4/2020)
https://www.washingtonpost.com/graphics/2020/world/corona-simulator/?mod=article_inline (2/4/2020)
https://www.washingtonpost.com/graphics/2020/world/mapping-spread-new-coronavirus/ (2/4/2020)
https://ourworldindata.org/coronavirus (2/4/2020)
https://www.rapidtables.com/ (26/4/2020)

{|references)}
