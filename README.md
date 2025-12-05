# Sight Reduction Calculator

Welcome to my Sight Reduction Calculator based on the Marc. St-Hilare Method for the Sun.

To get started, download the program from the "Projects" Tab and launch the program as adminstrator.<br>

<img width="471" height="406" alt="image" src="https://github.com/user-attachments/assets/dd6afc3a-6790-4da1-b15b-4ae96f658a01" />

## Instructions

You will need the following information:

**First Sight:**

_Date and Time in GMT_

_DR Latitude and Longitude_ <br>

<img width="658" height="359" alt="image" src="https://github.com/user-attachments/assets/78b5f4d5-f09e-417d-8c45-691145257fc1" /> <br><br>

The program will list your GHA, LHA, Declination, ABC values and Azimuth.

<img width="400" height="299" alt="image" src="https://github.com/user-attachments/assets/ba5e04d0-b1b3-4326-bd84-fb0da9a69328" /> <br><br>


Input your Sextant Altitude, Index Error, Height of Eye, Upper Limb or Lower Limb. <br>

<img width="944" height="140" alt="image" src="https://github.com/user-attachments/assets/5a5abef7-44f5-4c5a-8107-419cb5657a4a" /> <br><br>

The program will also give you your true altitude, TZX and CZX.

<img width="255" height="66" alt="image" src="https://github.com/user-attachments/assets/fd8a10ad-db67-476c-ab6b-63a3a1c2a9b9" /> <br><br>

Course and Distance for a Body Run Body<br>

<img width="490" height="46" alt="image" src="https://github.com/user-attachments/assets/7c1bf1a4-ea22-402b-b94c-ae52834e9626" /><br><br>

Course and Distance for Simultaneous Sights

<img width="465" height="47" alt="image" src="https://github.com/user-attachments/assets/5000ac17-173b-46eb-acd3-dc74f7ac5e3b" /> <br><br>


After inputting the same information about the second sight, the program will generate a matplotlib chart to visualize the Marc. St-Hilare plot.

<img width="521" height="525" alt="image" src="https://github.com/user-attachments/assets/8d289804-ed8e-44f2-8bb2-b68620d7afee" /><br><br>

It will also list your intercepts with bearings.<br>

<img width="1131" height="77" alt="image" src="https://github.com/user-attachments/assets/b24e73b6-ef73-4a04-bbbb-a81f487da8ae" /><br><br>


From the chart, the D'Lat and Departure is also listed along with the calculated final latitude and longitude.<br>

<img width="528" height="152" alt="image" src="https://github.com/user-attachments/assets/ff6aac29-abe0-4e7f-bd45-f8ffad0f3af2" />

# Math behind the calculator

As aforementioned, this calculator uses the Marc-St Hilare sight reduction method.

The azimuth is calculated with the ABC formulas listed below.

$$
a = \frac{\tan(\text{lat})}{\tan(t_)}
\qquad (3)
$$

$$
b = \frac{\tan(\text{dec})}{\sin(t_)}
\qquad (4)
$$

$$
c = \text{a}\pm\text{b}
\qquad (5)
$$

Dip is calculated by the formula below:

$$
\text{Dip} = 1.76 \sqrt{\text{Height of Eye}}
\qquad (6)
$$


Refraction is calculated using Bennnet's: The Calculation of Astronomical Refraction in Marine Navigation.

$$
\text{Refraction} =
\tan\left(
\text{Apparent altitude} + \frac{7.31}{\text{Apparent altitude} + 4.4}
\right)
\qquad (7)
$$

<br>

Semi Diameter and Parallax are implemented through a dictionary based on Norie's Nautical Table.

<br>

The Calculated Zenith Distance (CZX) is caluclated by:

$$
\cos(\text{CZX}) =
\cos(\text{Latitude}) \cdot \cos(\text{Declination}) \cdot \cos(t)
\pm
\sin(\text{Latitude}) \cdot \sin(\text{Declination})
\qquad (8)
$$

<br>

**The equations below are derived by me as normally the intercepts are plotted on graph paper.**

<br><br>

First, a range of y-values are calculated based on an array of x-values from [10,10] for the initial line.

$$
\text{y} = \tan(Azimuth) \cdot x
\qquad (9)
$$

<br>

Second, we have to obtain the y-intercept of both perpendicular lines, which represent our Line of Position (LOP).

$$
b = \text{intercept} \cdot \sin(Azimuth)
\-
\left(
-\frac{1}{\tan(Azimuth)}
\right)
\left(
\text{intercept} \cdot \cos(Azimuth)
\right)
\qquad (10)
$$

<br>

Third, we calculate our range of y-values for the perpendicular line below based on the same array of x-values

$$
\text{y}_{Perpendicular}\ =
-\frac{1}{\tan(Azimuth)}x + b
\qquad (11)
$$

<br>

Now that we have our LOPs, we can find the common x and y-values which correlate to our Departure and Difference in Latitude (D'Lat)

$$
\text{Departure} =
\frac{b_2 - b}{
-\cot(\text{Azimuth})
+
\cot(\text{Azimuth}_2)
}
\qquad (12)
$$

$$
D'\text{Lat} =
-\frac{1}{\tan(Azimuth)} \cdot \text{Departure}
+\ b
\qquad (13)
$$

<br>

Using a Plane Sailing Formula, we can turn the depature into a Difference in Longitude (D'Long)

$$
D'\text{Long} =
\frac{\text{Departure}}{\cos(MLat)}
\qquad (14)
$$

## Disclaimer

This calculator was built as a side project and should by no means be used as a primary positioning system. <br>
<tt>© Harry Leung, 2025, email: harryleung@live.ca</tt><br>
<tt>[MIT&nbsp;License](https://github.com/Leung-H/Sight-Reduction-Calculator/blob/main/LICENSE)</tt><br>
