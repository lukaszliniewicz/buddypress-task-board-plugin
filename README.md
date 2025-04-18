# Task Board Plugin for WordPress

A WordPress plugin that adds task management boards to your site via a shortcode.

## Overview

This plugin provides a way to display and manage simple task lists or Kanban-style boards directly within your WordPress pages or posts. It uses a shortcode, `[task_board]`, to render the board interface. You can create multiple distinct boards by specifying a unique `board_name` in the shortcode.

The interface allows logged-in users to view, add, edit, and manage tasks. It relies on AJAX for smoother interactions like adding tasks, comments, and updating statuses without full page reloads.

## Features

*   **Shortcode Driven:** Add a task board anywhere using `[task_board board_name="your_unique_board_name"]`.
*   **Multiple Boards:** Create different boards for different projects or contexts using unique `board_name` values.
*   **Task Management:**
    *   Create tasks with a name and description (using a basic TinyMCE editor).
    *   Set task status (Pending, In Progress, Done).
    *   Assign task priority (1-10).
    *   Organize tasks with categories (managed per board).
    *   Set optional deadlines using a datepicker.
    *   Assign tasks to one or more registered WordPress users (uses autocomplete search).
*   **Comments:** Add comments to tasks. Supports @mentioning other registered users (links to their profile/author page).
*   **Filtering & Sorting:** Search tasks by keyword, filter by status, and sort by name, priority, deadline, or status.
*   **User Assignment:** Search and select registered WordPress users to assign to tasks.
*   **BuddyPress Integration (Optional):** If BuddyPress is active, the plugin can add a "Tasks" tab to groups.
    *   Each group gets its own task board (using `board_name="group_X"` where X is the group ID).
    *   Group admins can enable/disable the Tasks feature in the group settings.
    *   User assignment searches BuddyPress members within the group context.
*   **Email Notifications:** Sends basic email notifications to users when they are assigned to a task or when a comment is added to a task they are assigned to.

## Installation

1.  Download the plugin ZIP file.
2.  Log in to your WordPress admin area.
3.  Go to `Plugins` -> `Add New`.
4.  Click `Upload Plugin` at the top.
5.  Upload the ZIP file you downloaded.
6.  Activate the plugin through the 'Plugins' menu in WordPress.

Alternatively, you can unzip the plugin and upload the `task-board-plugin` folder to your `/wp-content/plugins/` directory via FTP, then activate it from the Plugins menu.

## Usage

1.  Create a new Page or Post (or edit an existing one).
2.  Add the following shortcode to the content area:
    ```
    [task_board board_name="project_alpha"]
    ```
    *   **Important:** Replace `"project_alpha"` with a unique identifier for this specific board. Use lowercase letters, numbers, and underscores only. Each board needs a different `board_name`.
3.  Publish or update the Page/Post.
4.  View the page on the front-end. You should see the task board interface.

**Permissions (Standalone Boards):** For boards created directly on pages/posts using the shortcode (like `[task_board board_name="some_board"]`), the default behavior relies on the page/post visibility. Logged-in users who can view the page can generally interact with the board (add tasks, comments, etc.).

### BuddyPress Groups

If you have BuddyPress active with the Groups component enabled:

1.  When creating or editing a group, you will see an option to "Enable task board for this group".
2.  If enabled, a "Tasks" tab will appear in the group's navigation.
3.  This tab displays a task board specific to that group. The plugin automatically uses a `board_name` like `group_123` (where `123` is the group ID). You don't need to manually add the shortcode for group boards.
4.  User assignment within a group task board will primarily search members of that group.

**Permissions (BuddyPress Groups):** When used within BuddyPress groups, access control to the task board itself is primarily managed by the **group's settings**:
    *   In a **Private** or **Hidden** group, only members of that group will be able to access the "Tasks" tab and interact with the board.
    *   In a **Public** group, any site member might be able to view the tab (depending on BuddyPress settings), but interaction (adding tasks, commenting) typically requires group membership.
    *   The plugin leverages BuddyPress's existing group privacy and membership system for access control to the board. *Note: Within the board itself, there are currently no specific roles defined (e.g., task manager vs. regular user)*.

## Dependencies

*   WordPress (tested up to version 6.5)
*   PHP (version 7.4 or higher recommended)
*   jQuery (Bundled with WordPress)
*   jQuery UI (Datepicker, Autocomplete - Bundled with WordPress)
*   TinyMCE (Bundled with WordPress)
*   BuddyPress (Optional, but recommended for group-based task management and better permission handling)

## Limitations

*   Standalone boards (not in groups) have basic permission handling based on page visibility. The BuddyPress integration provides more robust access control via group membership.
*   Relies heavily on the WordPress/BuddyPress user system for assignments and comments.
*   No granular roles defined within the task board itself (e.g., admin vs. member).

## License

GPL v2 or later - https://www.gnu.org/licenses/gpl-2.0.html
