# LBL Flow

A local desktop FCS viewer with the same dark navy surfaces, muted rose accents, and compact three-panel layout as Panama Blot Analyzer.

The antibody emblem uses a paired rose stem and arms with shorter blue chains, suggesting an immunoglobulin. The app retains its navy and rose palette. Existing `.pflow` workspaces remain compatible.

## Open the app

Double-click the **LBL Flow** desktop icon or **Start LBL Flow.cmd** in this folder. Version 0.16.0 is in `dist/release-0.16.0/LBL Flow`. The Windows distribution includes Python and its dependencies. Keep the `_internal` folder beside the executable. The native window uses the installed Microsoft Edge WebView2 runtime.

For another Windows computer, run **LBL-Flow-0.16.0-Windows-x64-Setup.exe**. Setup includes Python, creates shortcuts and an uninstall entry, and installs Microsoft's WebView2 runtime if missing (internet required for that runtime step). Requires Windows 10/11, 64-bit. Alternatively extract **LBL-Flow-Windows.zip** and open **LBL Flow.exe**. Save and close the app before upgrading. Setup/uninstall leave saved workspaces and FCS files alone.

**Mac installers:** choose **LBL-Flow-0.16.0-macOS-arm64-Installer.zip** for Apple Silicon or **LBL-Flow-0.16.0-macOS-x86_64-Installer.zip** for Intel. Extract the entire ZIP and double-click **Install LBL Flow.command**. The offline installer includes Python and dependencies, creates **~/Applications/LBL Flow.app**, checks the runtime before completing installation, and keeps a previous installation when updating. Requires **macOS 12.3 Monterey or later**. It needs no admin account or internet. Mac dependencies, hashes and Mach-O minimum OS versions were checked on Windows, but native Mac installation and GUI operation have **not yet been verified on a Mac**.

The packages are unsigned; the Mac package is not Apple-notarized. macOS may require explicit approval in Privacy & Security. The installers do not disable OS security controls. For Mac font exports, installed system TrueType fonts are used where available; otherwise PDF uses the bundled fallback font.

Windows 7/8/8.1 cannot use the current supported WebView2 runtime. Older macOS versions are not included in this release. OS targets describe the intended minimum, not a claim that every OS release has been tested.

Press **F11** to enter fullscreen; press **F11** again to restore the window. This works independently in the main window and separate population windows, including the layout editor and settings dialogs.

## Gate, enter, repeat

1. Click **Import FCS** and select one or several `.fcs` files. You can also drop files on the plot. **Demo** opens a clearly labeled synthetic sample.
2. Choose Y and X parameters in the right panel. Fluorescence channels start with **Biexponential (logicle)**, which displays negative values; scatter and time start with **Linear**. Linear, Log10, Biexponential, and Asinh are available on either axis.
3. Choose **Rectangle** or **Ellipse** and drag over the population. For **Polygon**, click each vertex and double-click, press Enter, or click the first vertex to finish.
4. Name the population. **Double-click anywhere inside its gate** to open a separate population window. Each window keeps its own population and axes. Click a name in the **Population tree** to navigate within the current window instead.
5. Change the axes and draw another gate. Only events in the current parent can enter the new child population. Repeat as deeply as needed, up to 256 gates per sample.
6. Use **Parent** or the breadcrumb to go back. Select any population to see its exact count and percentage of parent and total.

**Plot type** offers density scatter, uniform-color dot plots, contour plots, and histograms. Contour intervals are 10%, 5%, or 2%, with optional outlier dots. Contours estimate equal-probability regions using a smoothed 160 x 160 histogram of all visible events; they are a display estimate and do not affect gate membership. Density and uncolored dot views show up to 35,000 deterministically sampled events. Colored dot views sample the background and colored populations separately, so rare highlighted populations remain visible (up to 70,000 displayed events total).

Select **Histogram** for a one-parameter plot and use **Range** to draw a one-dimensional gate. **Show** next to a child gate restores its original axes. The arrow opens that child in a new window. Gate outlines follow scale changes when the parameters and compensation match; curved outlines are sampled for display while exact membership stays in the original gate coordinates.

**Ellipses** (E): use one continuous drag. Start at one end of the population and drag along its length to set the angle; keep holding the mouse button and move sideways to set the width, then release. A straight stroke makes a tilted oval with a 2:1 length-to-width ratio, matching the observed FlowJo starting shape. Bending the same stroke to one side widens it; bending to the other side narrows it. Widen it until both dimensions match to make a circle; the tool gently snaps to round within 3 screen pixels, and Shift forces an exact circle at any angle. Click the gate to show its handles. Filled end handles adjust length and angle around the opposite end. Hollow side handles adjust thickness; corner handles adjust length and thickness together. The round handle rotates around the center. Drag inside to move the whole gate. Esc cancels a drag; Ctrl+Z undoes it. Existing two-corner ellipses keep their membership until edited.

**Quadrants** (Q): click to place the intersection and create four child populations. Drag the intersection to adjust all four together. Double-click a region to enter it and add nested gates. Quadrants extend beyond the displayed range and divide all plottable parent events without overlap. Upper quadrant labels sit at the top outside corners; lower labels stay at the bottom, in both the graph and exported figures. Events exactly on a split go to the right or upper side. Nonpositive values hidden by a logarithmic axis cannot be assigned on that axis.

**Population labels**: with Select (V), drag a population name and percentage to reposition just that label. The gate geometry, counts and child populations stay the same. Positions follow the plot proportionally in every open view, existing layout figures, resized figures and PNG/SVG/PDF exports. This works with rectangle, ellipse, polygon, range and individual quadrant labels. Escape cancels a drag; Ctrl+Z undoes it. Saved workspaces retain the positions.

**Delete**: click a gate on the plot, or select a population in the tree, then press Delete. It removes that gate and its descendants immediately; Ctrl+Z restores them. Deleting one quadrant leaves its siblings intact and linked. Typing in a field or using an open dialog does not delete gates.

## Copy gates and apply strategies

Ctrl+click gates in the population tree (or on the plot) to select several gates. Press **Ctrl+C** or **Copy**, select another sample, then **Ctrl+V** or **Paste**. Copied branches include descendants, required ancestors and linked quadrants. The clipboard is a snapshot and remains available across population windows until a new workspace is opened.

**Apply strategy…** copies the entire current sample's strategy to one or more targets. The dialog previews added, updated and removed gates. **Merge** updates matching population paths and adds missing gates; **Replace** removes target-only gates. Both preserve matching target gate IDs, colors, label positions and saved population displays. Channel matching uses detector names and marker labels; unresolved parameters need a manual match. Target compensation matrices are retained. An incompatible target blocks the whole operation. **Ctrl+Z** restores all targets together.

## Graph editor

Open **Graph editor → New graph**. The default is a **Bar / dot comparison**: population names on the horizontal axis, mean bars and one diamond marker per sample. Choose **% of parent**, **% of all events**, **Event count**, or count/percentage panels. Each category has its own population, samples, label and color. Use different populations, or the same population in separate sample groups.

Under **Categories on X**, use **+ Population** to add a bar and select its population and samples. **Error bars** starts at None; SD and SEM are optional. **Individual samples** shows points without filled mean bars. Markers spread horizontally to distinguish overlapping values; their vertical values remain exact.

The default **Clean figure** uses black axes, slanted category labels, muted bars, colored diamond markers and no grid, title, sample-count labels or caption. **Figure style** offers circles, a custom Y-axis label, and optional title/n/caption/grid. It stays expanded while settings are edited, and preserves focus and scroll position. Font choices are Arial, Times New Roman, Calibri and Georgia. Adjust axis/category/tick/title text sizes, bold labels, category-label angle, axis/tick/grid thickness, tick length/count/direction, sample-marker radius and bar width. Sizes and line widths are figure pixels; PNG scales them with export resolution. Font choices and styling carry through SVG, embedded-font PDF and PNG exports and saved workspaces. **Axes & appearance** provides linear/log scales, manual limits and white/navy backgrounds. PNG exports preserve the figure's aspect ratio at 3× resolution; SVG/PDF remain vectors.

For an existing XY graph, click **Bar comparison**: its X/Y populations become categories, using the selected sample union and Y measure. This conversion is undoable. **XY scatter** remains available for numerical population-versus-population plots. Saved graphs retain their settings until edited. Compensation tubes are excluded from default selections; they can be selected explicitly.

Counts use all acquired events in each gate; they are not a calibrated cell concentration. Population matching uses the complete gate ancestry and name. Missing/ambiguous gates and removed samples are reported and omitted, never treated as zero. A present gate with no events has count zero; percentages with a zero denominator are undefined. Nonpositive values are omitted on log axes. SD uses the sample standard deviation; SD/SEM are undefined for fewer than two samples.

Graph settings are saved with the workspace and counts update when gates change. Export **SVG**, **PDF**, **PNG** (3× figure size), or **CSV**. The data table and CSV include per-sample values and missing-population status. Graphs support undo/redo, duplication and deletion.

## Colors and population overlays

Click **Colors…** above a graph, or select a layout plot and click **Colors…**.

- Gate, contour and plain dot defaults use bordeaux. Additional gates on the same axes receive complementary colors. New gates on bordeaux contours use a contrasting palette color; choosing a similar custom contour color also triggers contrast. Plot and gate colors remain independently editable.
- Quadrants start with one color (bordeaux, or a contrasting color on matching contours). **Four colors** restores the rose/blue/sage/gold scheme; **Bordeaux** makes the group uniform. Each quadrant also has its own color picker.
- In a **Dot plot**, **Dot outline** adds a thin edge, black initially; its color is editable and the checkbox removes it. Outlines start off. **Default** restores the dot color to bordeaux; saved custom colors are preserved.
- In a **Dot plot**, **Colored populations → + Population** highlights any gate from the same sample, including nested populations made on different axes. Only events also in the displayed parent population are colored. For example, display total B cells and add a memory B-cell gate. The legend identifies the colored populations.
- Choose up to eight populations, change their colors, toggle them, remove them or reorder them. Later rows take precedence for events shared by overlapping gates. The colors use exact event identities and do not change masks or statistics. Rare colored populations are sampled independently of the background.
- Plot colors and population overlays belong to each display or figure plot; gate colors apply throughout the sample. Apply is one undo step; Cancel discards edits. Saved workspaces retain the colors. Legacy automatic colors migrate to the new defaults; custom colors are preserved.

## Reverse gating

Select a gate on the graph, or enter its population, then click **Reverse gate…** beside **Axes…** and **Colors…**. Choose a color (bordeaux initially) and **Apply**. If you are inside that population, its parent opens automatically. The selected cells then remain highlighted in every ancestor, including All events, across different axes and open population windows. The dialog also lets you choose another population, edit its color or **Turn off** its reverse gate.

Reverse gating works in 2D/3D density scatter and dot plots, contour plots and histograms. Density colors remain underneath the highlighted cells. Histogram views draw the selected population's counts as a colored trace. Dot backgrounds receive a contrasting muted color when their base color matches a reverse-gate color. A legend identifies each reverse gate. Layouts and SVG/PDF/PNG exports include the same highlighting.

Reverse gates use exact original event identities and update with gate edits. They do not change population membership, counts, density estimates or saved axis preferences. Highlights are drawn on top of the background, including in 3D; they are sampled separately so rare populations remain visible. Up to eight reverse gates per sample share an additional 35,000 displayed-point budget. Later gates in the population tree take precedence for shared events. Reverse colors are saved with the gates, apply throughout the sample, and support undo/redo. Deleting a gate removes its reverse highlight.

## Three-axis views

**Display → Axes → 3 axes · 3D** opens a rotatable X/Y/Z density plot of the current population. **Density** is the default when switching to three axes; **Plot type** also offers **Dot plot**. New samples still start with **2 axes**. Select Z, Y and X parameters and scales independently; **Axes…** includes the Z histogram, draggable limits and transform settings.

Drag to rotate, scroll to zoom, and double-click or use **Reset 3D view** to restore the camera. Rotation, zoom and camera reset reuse the current event coordinates and density colors without a population reload. Coordinates are normalized once for responsive dragging. Each completed movement is saved as one undoable display change. Switching from 3D to 2D retains the current X/Y parameters, scales and ranges and hides Z; switching back restores Z. Large dots remain available in both modes. Dot mode supports population colors and optional outlines. Gate drawing uses the two-axis view; switch back to 2 axes to create or edit gates, then inspect the resulting populations in 3D.

Add a 3D view to a layout with **+ Layout**. A selected layout plot offers **3D density** and **3D dot plot** in its Plot menu, a Z parameter and numeric rotation/tilt controls. Double-click opens the rotatable source view. SVG/PDF/PNG export the selected angle; SVG and PDF retain vector points, axes and labels.

3D density measures local concentration in the displayed, transformed X/Y/Z space using a smoothed 64 × 64 × 64 histogram of all visible events. The Gaussian smoothing width is one bin. Up to 35,000 dots are sampled after density is calculated. The low-to-high palette shows relative density within this view and stays unchanged while rotating or zooming the camera. Changing the population, axes, transforms or displayed limits recalculates density. This display estimate does not change gate membership or counts.

## Figure layouts

- Click **+ Layout** above a graph to add its current axes and dot size to a figure. **Layout editor** opens saved figures. **+ Plot** selects another sample/population; you can also drag a population from the tree onto the page.
- The editor caches lightweight point previews and batches pointer movement per animation frame. Moving, resizing, labels and arrows reuse the existing plots. SVG/PDF exports retain vector detail. Gate outlines are thicker, and population titles and gate names are larger and bold with a background halo.
- Drag a plot to move it; its lower-right corner resizes it without stretching the axes. Double-click a plot to open its source population.
- **Arrow**: drag between plots to connect them. Attached endpoints follow moved/resized plots. Drag endpoint handles to reposition or reconnect; drag on empty page space for a free arrow.
- **Text** adds editable labels. Select a plot to change its title, plot type, contour interval/outliers, or large-dot setting. Each figure plot keeps its own choices. Delete removes only the selected figure object; Ctrl+Z restores it. Duplicate copies an object.
- Page width/height are in pixels. White and navy pages, fit-to-page, and fixed zoom are available. **SVG** and **PDF** retain vector points, axes, gates, text and arrows. **PNG** supports 1x–4x resolution; the default 1200 x 800 page at 3x exports 3600 x 2400 pixels.
- Plots retain the view captured when added and update their events, counts and gates from the source population. Remove and re-add a plot to capture a different view. A deleted source is marked explicitly; replace/remove its plot before exporting.
- Layouts and population display preferences are included in the .pflow workspace. Changes in another window cannot silently overwrite a newer layout edit.

## Adjust the axes

**Large dots** in Display applies only to that window. Other open windows keep their own choice. Figure plots capture this choice and can change it independently.

On first entering a gate drawn on FSC-A/SSC-A, samples with CD5 and B220 markers open with CD5 on X and B220 on Y. Defaults match the open LBL example inspected on 2026-10-30: CD5 T=262144, W=1, M=5.82, A=0; B220 T=262144, W=1.59, M=6.16, A=0. These give raw limits about -64.954 to 262144 and -429.504 to 262144. Marker names/labels identify the channels; unrelated panels retain their existing view. Explicit custom parameter settings and saved population views take precedence. Each population remembers subsequent changes to its axes.

The Display panel lists Y parameter and scale before X. Click **Axes…**, or double-click either axis, to open its settings. The dialog lists Y before X too. The histogram previews events in the current population. **Drag either rose handle** to set the displayed minimum or maximum; shaded regions show what falls outside that range. For a histogram's Y axis, drag the count handles vertically.

Choose Linear, Log10, Biexponential or Asinh. With Biexponential, drag **Linear width**, **Negative decades**, and **Positive decades** sliders to reshape the live histogram. Numeric fields allow precise values. Changes are previews until **Apply axes**; Cancel leaves the workspace untouched. Applying both axes is one undo step.

New imports prefer FSC-A versus SSC-A on linear axes. **Suggested display limits** keep isolated acquisition spikes from compressing the main populations: scatter starts at zero and uses at least the recorded parameter range, expanding to a rounded 1.25 times the 90th percentile when necessary. Fluorescence has a stable transformed range rather than fitting its extreme events. Scatter plots stay square as the window resizes.

The axis dialog also offers **All sample values (including outliers)** and fitting the current population. **Auto range** clears the selected axis's custom limits. Manual limits are entered in original parameter units. The dashed blue line marks zero where that scale supports it. The preview reports events outside its domain.

For an older workspace, click **Reset display defaults** in the Display panel. It restores suggested ranges, parameter-specific scales, and a valid acquisition matrix for the current view, retaining its selected parameters. This is one undoable change. Existing gates retain their original coordinate definitions and counts; reset does not redraw them.

Biexponential uses the Gating-ML logicle implementation in [FlowUtils](https://flowutils.readthedocs.io/en/stable/api.html). Its adjustable parameters are top of scale **T**, positive decades **M**, linear width **W**, and negative decades **A**. It is distinct from FlowJo's legacy width-basis lookup-table transform. T starts from the FCS parameter range when selecting a fluorescence channel. Files identified as FACSDiva start with W=1, M=4.41854, A=0; other files use W=0.5, M=4.5, A=0. These are adjustable starting points, not imported FlowJo workspace settings.

Each tube remembers the scale, custom limits, and biexponential parameters for every channel you adjust. Switching from CD5 to FSC-A and back restores CD5's settings. These preferences are saved in the workspace and included in undo/redo. Reset display defaults resets the two currently selected parameters.

Axis changes affect the display; existing gate membership is preserved. Manual ranges crop the plot and histogram, not the population counts. The footer reports events outside the displayed range.

## Organize tubes and compensation controls

- **All tubes**, **Samples**, and **Compensation** filter the tube list. The two assigned groups are separate; All tubes contains every import.
- Following [FlowJo's default inclusion rule](https://flowjo.com/docs/flowjo10/setting-your-preferences/platforms/prefs-compensation), filenames or FCS `$FIL` values containing **comp** or **unstained** (case insensitive) go into Compensation. Other tubes go into Samples. Sample details show why a tube was assigned.
- Drag a tube onto Samples or Compensation, use the **Group** dropdown in Sample details, or tick several tubes and use **Move selected to…**. **Detect automatically** reapplies the filename rule. Manual assignments persist in saved workspaces.
- Click **×** beside a tube to remove it, or tick several and use **Remove** / **Delete**. **Ctrl+Z** restores the complete selection with its gates. Original FCS files are unchanged.
- Valid embedded spillover matrices are detected separately, marked **Matrix**, and applied automatically on new imports. Having a matrix does not make an experimental sample a compensation control. Use the Compensation selector to change this setting.
- Control grouping does not calculate a new spillover matrix from single-stain controls. A compensation wizard and importing external matrix files are not included in this version.

## Statistical comparisons

1. Open **Statistics → New comparison**, choose the population for each category, and select the samples belonging to Control/Treatment (rename these groups as needed). Use the same population with different sample subsets to compare experimental groups. Existing graphs appear in Statistics; **Edit groups & tests** opens their controls.
2. Expand **Statistical comparisons**. Add up to 12 comparisons. Choose Welch's independent t-test (default), Student's equal-variance t-test, paired t-test, Mann–Whitney U, Wilcoxon signed-rank, one-way ANOVA or Kruskal–Wallis. All pairwise tests are two-sided. ANOVA/Kruskal–Wallis are overall tests for two or more groups; an overall result does not identify which pairs differ. For specific pairs, add the planned pairwise comparisons.
3. For paired tests, choose **Same sample in both groups** for two populations measured in the same samples, or **Match samples manually** for separate matched tubes. Pairing uses explicit sample identities, never row order. Only complete pairs enter the test. Independent tests reject overlapping sample selections.
4. **Multiple comparisons** defaults to Holm correction; Bonferroni and no correction are available. The family contains all planned tests and all measures in this graph, including hidden brackets and temporarily unavailable tests. Count + percentage graphs therefore include both measures in the family. Unavailable tests contribute p=1 to adjustment and have no reported result.
5. Enable **Show bracket on graph**, then select asterisks, p-values or both. Stars use adjusted p when correction is enabled: * p < .05, ** p < .01, *** p < .001, **** p < .0001; ns otherwise. Brackets sit above the plot to avoid data overlap, including fixed/log axes. Font and line styling follows the graph. SVG/PDF/PNG retain the annotations. **Tests CSV** exports test names, actual n, means, differences, statistic/df, raw/adjusted p, pairing, inclusion/exclusion details, correction and calculation method.

One sample supplies one count or percentage. Each sample must represent a biological replicate; repeated technical tubes must not be treated as independent biological replicates. Event count is acquired events, not automatically an absolute cell concentration. Tests use untransformed values from full gate counts; changing the display scale does not change a test. Missing gates and undefined percentages are excluded and reported, never replaced with zero. At least two values per group/complete pairs are required. Undefined zero-variance tests display a reason and no stars. Test definitions are saved in the workspace; results are recalculated after data or gate changes.

Choose tests based on study design: Welch permits unequal variances but still relies on the sampling assumptions of a t-test; Student/ordinary ANOVA assume equal variances. Paired t-tests concern within-pair differences. Mann–Whitney tests distributions and only has a median/location interpretation under further shape assumptions; Wilcoxon assumes a symmetric distribution of paired differences. Kruskal–Wallis uses an asymptotic approximation and flags groups smaller than five. Sample independence cannot be established by the software. A nonsignificant result does not establish equivalence.

Calculations use SciPy. Small tied Mann–Whitney samples and small tied/zero-difference Wilcoxon samples use a deterministic permutation method (up to 9,999 resamples, seed 0); the actual method is recorded in results. Wilcoxon differences are rounded to 10 decimal places to avoid spurious floating-point ranks. No automatic normality screening or test switching is performed.

References: [SciPy t-tests](https://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.ttest_ind.html), [Mann–Whitney U](https://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.mannwhitneyu.html), [Wilcoxon](https://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.wilcoxon.html). Packaging: [Microsoft WebView2 distribution](https://learn.microsoft.com/en-us/microsoft-edge/webview2/concepts/distribution), [Python standalone runtimes](https://gregoryszorc.com/docs/python-build-standalone/main/running.html).

## Edit and save

- **Rename** changes a population's name.
- In **Explore** mode, click inside a gate and **drag it to move**. Click to select it and drag a square handle to resize; polygon handles move individual vertices. A complete drag is one undo operation. Descendant counts are recalculated and other open population windows refresh.
- **Redraw** opens its parent on the original axes; draw replacement geometry to recalculate it and all descendants.
- **Delete** removes a gate and its descendants; **Undo** restores them.
- **Save workspace / Ctrl+S** stores the original FCS files, gates, display settings, and selected population in one `.pflow` archive. The native app saves in place after the first save.
- **Save as** writes a separate copy. **Open workspace / Ctrl+O** restores a saved analysis. Undo history starts fresh after opening.
- Workspaces from versions 0.1 through 0.15.0 open in LBL Flow 0.16.0 with saved display settings and gates preserved. New saves use format version 15, including saved statistical comparisons and graph styling, and require LBL Flow 0.16.0 or later. Save the workspace in any old window before closing and reopening through the updated desktop icon.
- Closing the main window offers **Save & close**, **Discard changes**, or **Cancel** when the workspace is dirty. Canceling a save keeps the app open. Closing the main window also closes its population windows. Closing a population window alone preserves the shared workspace.
- **Statistics → Export CSV** exports counts, complete population paths, percentages, and gate settings for every sample.
- **Export these events** exports the current population's preprocessed numerical values and original one-based event indices. Values follow the currently selected compensation setting; display transformations are not applied to CSV data.
- **PNG** saves the current plot, axes, and visible gate outlines.

Keyboard: **V** explore; **R** rectangle; **P** polygon; **E** ellipse; **Q** quadrants; **G** histogram range; **Esc** cancel; **Ctrl+Z** undo; **Ctrl+Shift+Z** or **Ctrl+Y** redo.

## Interpretation and limits

- Gate counts use **all events**. Histogram bins include all events within the displayed range. Density and plain dot plots display at most 35,000 events, selected reproducibly for responsiveness; population-colored dot plots can show up to 70,000. The 2D density estimate uses the displayed sample; 3D density uses all events within the displayed XYZ limits before sampling dots. Both show relative density in the current transformed view.
- Children are the intersection of their geometry and their parent's membership. Boundaries are inclusive. Sibling gates may overlap; their percentages need not sum to 100%. Percentages with an empty denominator are shown as `—`.
- Gate geometry is stored in the original transformed coordinate system, together with axes, scale, cofactor, and compensation mode. Changing the display does not silently alter earlier gates.
- **Asinh** uses `asinh(value / cofactor)`, with default cofactor 150. **Log10** excludes values less than or equal to zero; excluded events are reported beneath the plot. Non-finite values cannot pass a gate on an affected axis. A gate that extends into nonpositive coordinates cannot be fully overlaid on a Log10 plot; Biexponential or Asinh supports its full boundary.
- FCS import uses [FlowIO 1.4](https://flowio.readthedocs.io/en/latest/api.html), including its gain, acquisition-log, and time preprocessing. FCS 2.0, 3.0, and 3.1 are supported. Malformed offsets, unsupported data, and invalid metadata are reported rather than silently reinterpreted. Multiple-dataset FCS files are not supported by this first release.
- New imports apply a usable embedded `$SPILLOVER`, `$SPILL`, or compatible `$COMP` matrix automatically. Saved workspaces retain their chosen compensation setting. Observed row vectors are corrected with the inverse spillover matrix, leaving source values unchanged. If an external workflow has already compensated the recorded data, turn compensation off to avoid applying it twice.
- Limits: 512 MB per FCS file, 1 GB source data per workspace, 256 samples, 256 gates per sample. Large files require additional RAM for decoded arrays and masks. No server upload or external account is used.
- This version does not import `.wsp`, apply gate templates to batches, calculate compensation matrices from controls, or provide Boolean gates or Gating-ML import/export. Validation does not establish clinical or instrument-specific equivalence.

## Development

```text
.venv\Scripts\python -m pip install -r flow-requirements.txt
.venv\Scripts\python flow_main.py
.venv\Scripts\python flow_main.py --demo
.venv\Scripts\python flow_main.py --browser
.venv\Scripts\python flow_main.py --serve --port 8782
.venv\Scripts\python -m pytest tests/test_flow.py -q --basetemp qa/flow-tests
powershell -ExecutionPolicy Bypass -File build-flow.ps1
```

The command line also accepts FCS paths or a `.pflow` path. The original Panama Blot Analyzer launcher and implementation remain separate.
