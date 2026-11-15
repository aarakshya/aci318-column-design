# RC Column Design to ACI 318

A browser calculator for rectangular tied concrete columns, designed to ACI 318-25 or 318-19 in SI units. Enter the section, materials, factored actions, bars and ties, click Calculate, and it works through slenderness, axial load with biaxial bending, shear, ties and lap splices. Every step shows the formula, the numbers used and the code clause, and each check is marked pass or fail.

## What it checks

- Materials and cover: minimum f'c, maximum fy and fyt, and cover for the chosen exposure (Table 20.5.1.3.1)
- Longitudinal steel: 1% to 8% of Ag (10.6.1.1), at least 4 bars (10.7.3.1) and clear spacing (25.2.3)
- Slenderness about each axis: kℓu/r against the limit of 6.2.5.1, then moment magnification with (EI)eff, Pc, Cm, M2,min and δ (6.6.4.5), the Pu < 0.75Pc stability check and the 1.4 limit on second-order moment (6.2.5.3)
- Axial load and bending: φPn,max for a tied column (22.4.2.1), uniaxial strength about x and y at Pu, and a biaxial check by strain compatibility with an inclined neutral axis
- Shear in each direction: Vc with axial compression (Table 22.5.5.1), Vs from the tie legs, the section size limit, minimum shear steel, spacing, and shear on both axes (22.5.1.10 and 22.5.1.11)
- Ties: diameter, spacing, clear spacing, and the number of legs needed for lateral support of the bars (25.7.2)
- Lap splice: compression lap or Class B tension lap, chosen from the bar stress at Pu (10.7.5.2, 25.5)

The results page draws the interaction diagram about each axis and the Mx-My contour at Pu with the factored actions marked. After each calculation, the input panel shows the steel ratio and utilisation next to the bars, and the largest tie spacing and the legs needed next to the ties. The page ends with a summary table, a cross-section and elevation drawing of the reinforcement, and a bar schedule. You can export the full calculation as a PDF or an Excel workbook.

## How to use it

Open `index.html` in a web browser. Nothing needs installing, and everything runs on your computer, so no data leaves the page. The PDF and Excel libraries are in the `lib` folder.

Axes: x is parallel to the width b, and y is parallel to the depth h. A moment about x bends the column over the depth h. Bar counts on each face include the corner bars.

To put it online, turn on GitHub Pages for this repository (Settings, then Pages, then deploy from the main branch).

## Limits

- Rectangular tied column with one bar size placed evenly on the four faces.
- Axial compression only, normal-weight concrete, uncoated bars, no transverse load between the column ends, nonseismic design.
- In a sway frame, enter end moments that already include the sway magnification. The calculator adds only the effect along the column length (6.6.4.6.4).
- The lap length comes from the one load case entered. Run the combination with the least axial load and the most moment before fixing it.
- Not covered: circular and spiral columns, axial tension, joint shear, column to footing dowels, offset bars and the seismic detailing of Chapter 18.
- For ACI 318-25, the one coded difference is the φ limit of 21.2.2.3 between 0.1f'cAg and Pn,bal. Slenderness, shear, ties and straight-bar laps follow the 318-19 form, and the 2025 lower bound on Vc is not used. Check them against the 2025 text before relying on them.

This is a design aid. Results should be checked by a qualified engineer.

## Third-party libraries

- [jsPDF](https://github.com/parallax/jsPDF) and [jsPDF-AutoTable](https://github.com/simonbengtsson/jsPDF-AutoTable), MIT licence
- [SheetJS Community Edition](https://github.com/SheetJS/sheetjs), Apache 2.0 licence
- [DejaVu Sans](https://dejavu-fonts.github.io/) font, subset and embedded for PDF output, free licence

Developed by Aarakshya Kandel
