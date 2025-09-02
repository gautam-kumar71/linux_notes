
# Vimium C Shortcuts Guide

## Basic Navigation Shortcuts:

- **`h`** → Scroll left
- **`j`** → Scroll down
- **`k`** → Scroll up
- **`l`** → Scroll right
- **`d`** → Scroll down a full page
- **`u`** → Scroll up a full page
- **`gg`** → Scroll to the top of the page
- **`G`** → Scroll to the bottom of the page
- **`w`** → Scroll down one full line
- **`b`** → Scroll up one full line
- **`H`** → Go back in history (similar to Back button)
- **`L`** → Go forward in history (similar to Forward button)

## Link Selection Shortcuts:

- **`f`** → Enter **link hint mode** (select links on the current page by typing their 2-letter hint)
- **`F`** → Same as `f`, but opens the link in a **new tab**.
- **`y`** → Copy the **URL** of the current page to the clipboard.
- **`gf`** → Focus the link under the cursor (move the cursor to the link).
- **`gi`** → Focus on the first input field on the page.
- **`gI`** → Focus on the last input field on the page.

## Tab Management Shortcuts:

- **`t`** → Open a **new tab**.
- **`T`** → Open a **new tab in background**.
- **`x`** → Close the current tab.
- **`X`** → Close all tabs except the current tab.
- **`gt`** → Switch to the **next tab**.
- **`gT`** → Switch to the **previous tab**.
- **`g0`** → Switch to the **first tab**.
- **`g9`** → Switch to the **last tab**.

## Scrolling and Content Navigation Shortcuts:

- **`/`** → Start **search** (similar to Find command)
- **`n`** → Move to the **next search result**.
- **`N`** → Move to the **previous search result**.
- **`gg`** → Jump to the **top** of the page.
- **`G`** → Jump to the **bottom** of the page.
- **`f`** → Find the next visible link on the page.
- **`F`** → Open the link in a new tab.

## Miscellaneous Shortcuts:

- **`:`** → Open the **command line** for Vimium commands (search, open, etc.)
- **`r`** → **Reload** the current page.
- **`u`** → **Undo** last action (reload, tab, etc.)
- **`Ctrl + f`** → Open the **find bar** to search the page.
- **`Ctrl + d`** → Bookmark the current page.
- **`b`** → Go to the **backward history** (back to the last page).
- **`F`** → Open the current link in a **new background tab**.
 - You can also press **`gi`** to focus the first input field on the page (sometimes it's the search bar).
## Custom Key Mappings:

You can create custom shortcuts by adding key mappings in **Vimium C**. Here’s how to do it:

1. Open **Vimium C Options** by clicking on the Vimium C icon → **Options**
2. Scroll down to **"Custom key mappings"**
3. Add your desired custom shortcuts here. For example:
   - **`map ,1 runJS var l=document.querySelector('a[jsname="UWckNb"]');if(l)l.click()`** (Opens the first Google search result)
   - **`map ,2 scrollTo(0, document.body.scrollHeight)`** (Scroll to the bottom of the page)

Then click **Save Changes** to activate them.

## Bonus Custom Commands:

- **`map`** → Create a new key mapping.
- **`unmap`** → Remove a custom key mapping.

---

## How to Turn Off Vimium on Certain Sites:

If you want to disable Vimium on specific websites, you can do the following:

1. Open **Vimium C Options** → **Advanced Options**.
2. Scroll down to **"Enable Vimium on certain websites"**.
3. In the **"Exclude these sites"** field, enter the URL or domain of the sites you want to exclude from Vimium. For example:
   - **`*.example.com`** to exclude all pages on the `example.com` domain.
1. Click **Save Changes** to apply.


checking if the git is working or not

