Analyze only the Group module of the Apora Flutter project.

Do NOT modify any other feature.

Current issues:

1. The Groups screen keeps showing "Loading..." forever.
2. Existing groups are not displayed.
3. Create Group works but the created groups do not appear.
4. Users cannot properly load into the Groups list.
5. Group chat needs a "Hide Chat" option.

---

## Fix Group Loading

Find the exact root cause.

Verify:

* Firestore queries
* Stream listeners
* Providers
* Repository
* Authentication state
* Current user UID
* Group membership filtering
* Firestore indexes
* Null checks
* Loading state logic

Ensure that:

* Loading stops after data is received.
* If there are no groups, show "No Groups Yet" instead of infinite loading.
* Existing groups appear immediately.
* Newly created groups appear instantly without restarting the app.
* Pull-to-refresh works correctly.

---

## Fix Group Membership

Verify that:

* Current user is included in the members list.
* Firestore stores member UIDs correctly.
* Group queries return only groups where the current user is a member.

---

## Hide Group Chat

Add a WhatsApp-style "Hide Chat" option.

When the user long-presses a group chat:

Show a bottom sheet with:

* Hide Chat
* Mute Notifications
* Pin Chat
* Delete Chat (Leave Group if applicable)

Hide Chat should:

* Remove the group from the main Groups list for that user only.
* Do NOT delete the group from Firestore.
* Do NOT remove other members.
* Save the hidden state locally or in the user's document.
* Add a Settings option:
  "Hidden Chats"
  where hidden groups can be viewed and restored.

---

Run:

flutter analyze

Fix every warning and error related to the Group module.

Generate a new Release APK after all Group issues are fixed.

Do not modify any working features outside the Group module.
