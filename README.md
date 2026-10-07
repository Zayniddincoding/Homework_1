# Student Scholarship Website

A responsive page presenting the state scholarship recipients of Termez State Pedagogical Institute for the 2025/2026 academic year.

## Project links

- [View the completed work](https://www.terdpi.uz/page/view/99)
- [Project conversation and development history](https://chatgpt.com/share/6ac5ebac-ebf4-83eb-b6d7-bff2a359ee7a)

## About the project

The page presents 12 students in the order of the supplied profiles. It includes each student's photo, name, scholarship, study program, degree level, year of study, and academic supervisor. The three empty student placeholders have been removed.

The code is designed for insertion into an existing website through the editor's Source / HTML mode. It uses HTML, CSS, and a small JavaScript script. No framework, package installation, database, or build process is required.

## Code files

| File | Purpose |
| --- | --- |
| `student-website-hidden-headings.html` | Uzbek version with photo header cropping and a student information popup. |
| `student-website-english.html` | English version of the page. |
| `student-website-russian.html` | Russian version of the page. |

These are alternative versions. Use one version on a page rather than pasting multiple versions together. Student names remain in their original spelling.

## Features

- Twelve student profiles with the supplied photo links.
- Three columns on wider screens, two on medium screens, and compact cards on phones.
- Scholarship labels and academic information.
- A “View student details” control that opens a popup with the student's photo and information when JavaScript is retained and allowed to run.
- A close button, outside-click closing, and Escape-key closing for the popup.
- Keyboard focus management inside the popup.
- Expandable information within the card when JavaScript is unavailable and the editor retains the HTML `details` and `summary` elements.
- Photo cropping to hide the top band containing the institute and ministry headings.
- Scoped CSS and explicit colors to reduce conflicts with the existing website theme.

Search controls and the additional institute navigation header were removed as requested.

## How to add the code to the website

1. Open the HTML file for your preferred language in a text editor, such as Notepad or a code editor.
2. Copy the complete contents of the file.
3. Open the target page in your website administration panel.
4. Switch the page editor to **Source / HTML** mode.
5. Replace the previous student-page code with the copied code. Keep a backup of the previous code before replacing it.
6. Save the page and open its visitor-facing URL.
7. Check the student cards, photos, popup, and phone layout.

The files are HTML fragments for an existing website. Your website template supplies the outer document structure and viewport settings. For a separate standalone page, place the fragment in a complete HTML document with UTF-8 encoding and this viewport tag in the head:

```html
<meta name="viewport" content="width=device-width, initial-scale=1">
```

## How the code works

### HTML

All 12 student cards are written directly into the HTML. The cards remain visible without JavaScript.

The main component uses `id="terdpi-scholarships"`. Each student card contains a photo area, a scholarship label, a name, study information, and an expandable details section.

### CSS

Styles are scoped under `#terdpi-scholarships` to reduce their effect on the rest of the website. Media queries adjust the layout for smaller screens. Some declarations use `!important` to resist conflicting theme styles.

The images are visually cropped through CSS. The original image files on the server are not changed.

### JavaScript

The script listens for a click on the details control, copies the selected student's photo and information into the popup, and displays it. It also handles closing and keyboard focus.

The popup does not use the HTML `dialog` element, which the website editor previously changed. The script checks that its required elements exist before attaching events.

## How to change a student photo

Find the student's image tag and replace its `src` value:

```html
<img
  src="/kcfinder/upload/images/your-student-photo.jpg"
  alt="Student full name"
  loading="lazy"
>
```

You can also use a complete server URL:

```html
<img
  src="https://www.terdpi.uz/kcfinder/upload/images/your-student-photo.jpg"
  alt="Student full name"
  loading="lazy"
>
```

Use the real uploaded file path. Relative paths beginning with `/kcfinder/` resolve on the website hosting the page; they usually do not display correctly when opening the file directly on your computer.

The popup copies the image from the card, so changing the card's image also changes the popup photo.

## How to edit student information

Find the student's name in the HTML, then edit the text in that card:

- Scholarship label: the element with class `badge`.
- Full name: the `h3` element.
- Study program: the element with class `program`.
- Degree, study year, and academic year: the element with class `course`.
- Supervisor and award information: the section with class `terdpi-info-content`.

Keep the surrounding HTML tags and class names. They connect the content to the layout and popup behavior.

## How to change the student order

Move a complete `<div class="card">...</div>` block to its new position inside the element with `id="grid"`. Update the number shown in the element with class `number`.

Keep every student card complete, including its image, information, and details section.

## How to add or remove a student

To add a student, copy a complete card and replace its information and photo. To remove a student, delete that student's complete card block.

The recipient and scholarship category totals in the introductory panel are static. Update them manually whenever the number of students or scholarship categories changes.

## Photo cropping

The current cropping is intended for the supplied poster-style photos. It hides the top strip with ministry and institute headings in both the cards and popup.

Look for the comment about hiding the ministry/institute header band. The cropping rules use `clip-path`, `transform`, and a popup photo frame.

If you replace a poster with a normal portrait, remove or adjust those cropping rules so the student's face is not cropped unnecessarily. Different image proportions may require different crop values. Check all photos on both desktop and phone screens after changing them.

## Language versions

The English version uses “View student details” and “Close”. The Russian version uses “Подробнее о студенте” and “Закрыть”. The Uzbek version uses “Batafsil tanishish” and “Yopish”.

Each file contains its own translated page text. There is no automatic language switcher.

## Troubleshooting

### The student cards are missing

Use the latest version, where cards are included directly in the HTML. Confirm that the editor has retained all 12 card blocks and that you pasted the complete file.

### The popup does not open

Your editor may remove or rewrite JavaScript, or the website may block inline scripts. Check whether the saved page still contains the script and popup elements. If inline scripts are blocked, the site administrator can move the script to an approved JavaScript file or template location.

The card details can still expand without JavaScript if the editor preserves `details` and `summary`.

### Photos do not load

Open the photo URL directly to confirm that it exists and is accessible. Check spelling, filename, extension, and server path. Use HTTPS photo URLs on an HTTPS page.

### Colors or spacing look different

The site theme or editor may override or remove styles. Confirm that the complete style block is preserved. Clear the page cache and reload. If needed, place the component styles in the website's approved stylesheet.

### The phone layout looks too wide

Confirm that the website template includes a viewport tag and that the mobile media queries are retained. A fixed-width parent container in the existing site may also need adjustment.

## Content note

For student 12, the original poster gives the surname as `Xudoyberdiyeva`, while the caption gives `Xudoynazarova`. The code currently uses the poster spelling and includes a verification note. Confirm the correct surname, then update the name and remove the note.

## Validation and limits

The generated code was checked for 12 student cards, preserved photo paths, unique popup IDs, and JavaScript syntax. Its final behavior inside the live website editor and on a physical phone has not been verified here.

## Completed work

[View the completed work](https://www.terdpi.uz/page/view/99)
