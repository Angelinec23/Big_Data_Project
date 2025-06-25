# :movie_camera: Exploration of Beauty Standards and Age in Film (1970s-2020s)
The title "Exploration of Beauty Standards and Age in Film (1970s–2020s)" reflects our central inquiry into how film industries, particularly Hollywood, have portrayed ideals of ***female beauty and age*** over time. The motivation for this project stems from increasing public discussions around media representation, ageism, and racial inclusivity. Despite growing awareness, mainstream films have historically favored narrow beauty norms—prioritizing youth, whiteness, and slim body types. By leveraging big data tools to analyze leading actresses’ physical and demographic attributes across decades, our project seeks to uncover how these standards have changed—or remained static—amid broader societal shifts.

## :woman_dancing: Project Description
This project investigates the evolution of beauty standards and age representation among ***leading actresses*** in the film industry, spanning from the 1970s through the 2020s. By leveraging comprehensive datasets from IMDb and detailed appearance data sourced from celebrity databases, we examined a range of physical characteristics—height, BMI, hair and eye color, skin tone—as well as the age at which actresses reached peak popularity ***(“pop age”)*** within each decade. Employing data filtering, integration, and visualization in R, our analysis uncovers notable shifts: while some longstanding ideals persist, there has been a measurable increase in diversity regarding race, body image, and age representation. These findings highlight both the enduring influence of traditional beauty norms and the emergence of a more inclusive cinematic landscape over the past fifty years.

##  :clapper: Getting Started

Our project is available on GitHub, and you can run the code directly in your R environment or IDE. This guide will help you get started with filtering the actress data and exporting it to an Excel file.

***Data Filtering***
1. **Download the Dataset from Kaggle**
- The combined dataset used in this project comes from Kaggle. You can download it by visiting the Kaggle page below.
     - Dataset Title: [IMDb Actors and Movies](https://www.kaggle.com/datasets/rishabjadhav/imdb-actors-and-movies/data?select=combined.csv)
- Click the link, and download the $${\color{lightgreen}combined.csv}$$ file to your computer.

2. **Set up Your R Environment**
- Install the necessary libraries in R:
  
  ![Step 1](https://github.com/user-attachments/assets/02eba314-08ff-4f7e-b06e-06687c27ffb7)
    - If you are using RStudio or another IDE, open a new R script and set up the environment.
 
3. **Load the Dataset**
- Save the $${\color{lightgreen}combined.xlsx}$$ file to a known location on your computer. You will need to specify the correct path in the code.

> [!NOTE]
> In your R script, set the path to the file like so:

    file_path <- "path_to_your_file/combined.xlsx"  # Replace with the actual file path
    data <- read_excel(file_path)

4. **Filter Actresses from Data**
> Run the following R code to filter the dataset for actresses based on their profession:

    actresses_data <- data %>% filter(grepl("actress", primaryProfession, ignore.case = TRUE))
- This step will create a new dataset $${\color{lightgreen}actresses_data}$$ containing only individuals whose profession includes "actress".

5. **Export the Filtered Data to Excel**
> After filtering the data, you can export it to a new Excel file using the following command:

     write_xlsx(actresses_data, "path_to_save/actresses_data.xlsx")  # Specify the path where you want to save
- This will create a new Excel file $${\color{lightgreen}actresses_data.xlsx}$$ in your specified location

## :open_file_folder: File Structure

[Describe the file structure of your project, including how the files are organized and what each file contains. Be sure to explain the purpose of each file and how they are related to one another.]

## :chart_with_upwards_trend: Analysis

[Describe your analysis methods and include any visualizations or graphics that you used to present your findings. Explain the insights that you gained from your analysis and how they relate to your research question or problem statement.]

## :dart: Results

In our project *Exploration of Beauty Standards and Age in Film (1970s–2020s)*, we set out to examine how visual and demographic representation among leading actresses has evolved over time. Using a combination of large-scale datasets and analytical R scripts, we assessed trends across race, age, physical traits (height, weight, BMI), and visual features (hair color, eye color, skin tone) among top actresses in each decade.

## **H₁: “Each decade has a dominant beauty cluster.”**

* **Test:** χ² test of independence between Decade and Cluster

* **Result:** Χ²(10) \= 13.253, p \= 0.2099

* **Interpretation:**

  * Because p \> 0.05, you **fail to reject** the null of independence. There’s **no statistically significant** association between decade and which cluster an actress falls into.

  * In other words, although the bar-fill plot shows some visual shifts (e.g. Cluster 3 dominating the ’90s), those differences aren’t strong enough, given your sample sizes, to conclude a real change in “dominant” beauty clusters across decades.

* **Conclusion for H₁:** **Not supported** by the χ² test at α \= 0.05. There isn’t enough evidence to say that any one beauty “cluster” truly dominates in one decade versus another. However, there’s a feature that dominates each year.   
![Image 2025-6-24 at 16 34 (1)](https://github.com/user-attachments/assets/40386fc3-eebc-492a-bcf3-71385c80ff7b)

**Explanation of the cluster:**

| Cluster | n | MeanAge | MeanHeight | MeanWeight | MeanBMI | MeanSkinType | TopEye | TopHair | TopRace |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| 1 | 20 | 45.3 | 168.4 | 64.2 | 22.7 | 3.1 | Brown | Brown | White |
| 2 | 45 | 32.1 | 172.5 | 58.3 | 19.6 | 2.4 | Blue | Blonde | Caucasian |
| 3 | 55 | 27.4 | 165.0 | 52.1 | 19.1 | 1.8 | Brown | Black | Mixed |

From that you can craft human-readable definitions, for example:

* **Cluster 1 (“Mature Classics”)**

  * Oldest on average (mid-40s), higher BMI (\~22.7), medium height (\~168 cm)

  * Predominantly brown hair & eyes, mostly White/Caucasian

* **Cluster 2 (“Tall Slim Blonds”)**

  * Mid-30s average age, tallest on average (\~172 cm), lowest BMI (\~19.6)

  * Largely blue-eyed and blonde, largely Caucasian

* **Cluster 3 (“Youthful Petite Mix”)**

  * Youngest group (late-20s), shortest (\~165 cm), lightest weight (\~52 kg), low BMI (\~19.1)

  * Brown eyes, darker hair colors, and more racial/ethnic diversity

## **H₂: “Youth-centered clusters (actresses under 30\) dominate more consistently in recent decades.”**

1. **Descriptive trend** (proportion under 30 by decade):

   * Rises from \~35 % in 1970 up to \~85 % in 2010, then dips to \~60 % in 2020\.

2. **Logistic regression** (Youth \~ Decade):

   * **Coefficient (Decade):** 0.0005852

   * **Std. Error:** 0.0002003

   * **z \= 2.922, p \= 0.0035**

   * Since p \< 0.01, there’s a **highly significant** positive association: as you move from earlier to later decades, the odds of an actress being under 30 **increase**.

   * In plain terms, each incremental year (the way you’ve coded Decade) is associated with a small but statistically significant rise in the likelihood of “youth.”

3. **Conclusion for H₂:** **Supported.** There is a significant upward trend in the proportion of under-30 actresses over time. **H₂ is confirmed**, but note the slight drop in 2020, consider whether sample size or external events (e.g., selection biases) could explain that dip.
   

![Image 2025-6-24 at 16 34](https://github.com/user-attachments/assets/40e8ef45-7ce9-448a-9b02-cb0627f44299)


**Example Case Study**

In 2023, Disney faced criticism for its approach to inclusion when it cast Halle Bailey, whose performance and advocacy have made her a prominent voice for the Black community, as Ariel in its live-action remake. While many praised Disney for giving a platform to a talented, underrepresented actress, some viewers argued that simply “re-skinning” an originally white character overlooks deeper issues in the studio’s history of privileging lighter skin tones. Critics suggested that Disney could have promoted genuine diversity by creating new, original stories and characters, rather than recasting established white-skinned icons, a strategy some dismissed as mere **“blackwashing”** rather than true, substantive inclusion. Additionally, the criticism regards the **“brownwashing”** of Snow White in 2025.



### **Key Findings:**

* **Racial Diversity**: Our results show a clear shift toward greater racial diversity in recent decades. While White actresses overwhelmingly dominated from the 1970s to the 1990s, the 2020s featured a marked increase in the representation of **Black**, **Asian**, and **Hispanic** actresses.

* **Hair and Eye Color Trends**: Brown hair and brown or blue eyes were most common overall. However, increases in brown eyes and darker hair colors in later decades suggest growing inclusion of actresses from diverse ethnic backgrounds.

* **Skin Tone (Fitzpatrick Scale)**: Lighter skin tones (Type II) were most dominant, especially in earlier decades. Recent data shows a broader distribution, with **Types IV and V** (medium to dark brown skin tones) becoming more common.

* **Physical Traits Over Time**:  
  * **BMI** remained within the healthy range across decades, with slight fluctuation (19.4–20.5).  
  * **Height** peaked in the 1990s and declined in the 2020s, suggesting changing beauty ideals.  
  * **Age** (Pop Age) increased in the 2020s, pointing to the industry’s growing openness to older actresses.

* **Race-Specific Patterns**:  
  * Asian actresses were leanest, with lower BMI and shorter height on average.  
  * Black actresses had slightly higher BMI values.  
  * White actresses showed the most variation in body traits, including outliers at both ends of the spectrum.

### **Conclusion:**

Our analysis confirms that **beauty standards in film have diversified over time**, particularly with respect to **race, skin tone, and body type**. While some traditional norms, such as slimness and fair skin, persist, the data indicates **a broader acceptance of different appearances** in contemporary casting. This shift aligns with increasing cultural and social awareness of inclusivity and representation.

### **Implications and Recommendations for Future Research:**

* **Representation Equity**: While diversity has improved, future research could explore **screen time, roles, and pay equity** across racial and age groups to determine whether representation translates into equal treatment.

* **Intersectionality**: Future studies should analyze how **intersections of race, age, and body type** affect career longevity, typecasting, and public reception.

* **Audience Perception**: Qualitative studies could examine how shifts in casting impact **audience attitudes and expectations**, particularly across global markets.

* **Behind the Camera**: Expanding the dataset to include **directors, writers, and producers** could uncover whether increasing diversity in creative leadership correlates with the casting trends we observed.

### **How Our Findings Address the Research Question:**

Our central research question focused on how beauty standards and age representation among top actresses have evolved across decades in the film industry. Through data-driven analysis of demographic and physical attributes, we have demonstrated **clear trends of increasing inclusivity**, suggesting that industry norms are shifting, albeit gradually, toward more **authentic and diverse representations of women**.

Ultimately, this project offers a foundation for understanding how cultural pressures and social progress shape the visual narratives presented in film.

## :people_hugging: Contributors

| Thanaphon Tatinij 113zm1010 田子芃 | Data cleaning, Data Collection, Poster |
| :---- | :---- |
| Angeline Chong Jia Lin 111zu1042 張嘉琳 | Data collection, Poster, READ.ME file |
| Pornnapat Pumipruek 111zu1050 王長婷  | Data collection, Data analysis, Presentation |
| Ratchadaporn Leungphetngam 111zu1051 陳秋天 | Data cleaning, Data filtering, Presentation slides  |
| Jehud Neri Sabbat 111zu1035 沙杰武 | Data cleaning, Data visualization, Github Set up |

## :man_teacher: Acknowledgments

We would like to express our heartfelt gratitude to Professor Pien Chung-Pei, our instructor for the *Big Data for Social Analysis* course, for his invaluable guidance and support throughout the development of our project, *Exploration of Beauty Standards and Age in Film (1970s–2020s)*. His insights and expertise played a crucial role in shaping our approach and helping us navigate various challenges during the research process.

We are also deeply thankful to the other student teams who offered their support and encouragement along the way. Their collaboration, constructive feedback, and shared resources significantly enhanced the depth and quality of our analysis.

Finally, we would like to extend our sincere appreciation to every member of our team. Your dedication, perseverance, and collaborative spirit were essential in bringing this project to life. Through your collective efforts, we were able to conduct a meaningful exploration of media representation using big data methods.

## :bookmark_tabs: References

Data Sources:
* Actor Data: https://www.kaggle.com/datasets/rishabjadhav/imdb-actors-and-movies/data
* Movie Data: https://www.kaggle.com/datasets/raedaddala/top-500-600-movies-of-each-year-from-1960-to-2024

Supplemental References:
* SnowWhite reference: https://www.bu.edu/articles/2025/new-snow-white-controversy/#:~:text=First%20there%20was%20the%20racist,arrive%20via%20a%20handsome%20prince.
* Little Mermaid reference: https://www.thepostathens.com/article/2023/06/little-mermaid-remake-review

