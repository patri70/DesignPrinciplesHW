# Streaming App — Design Patterns

A Java project that demonstrates two classic design patterns 
in the context of a video streaming platform (think YouTube/Netflix).

---

## Observer Pattern

**Problem:** When a new video is uploaded, all subscribed users 
need to be notified automatically.

**Solution:** `VideoChannel` acts as the Subject — it maintains 
a list of subscribers and notifies them when a new video is uploaded. 
`UserSubscriber` acts as the Observer — it reacts to the notification 
by printing a message. Users can subscribe and unsubscribe at any time,
and the channel doesn't need to know anything about them in advance.

---

## Decorator Pattern

**Problem:** A video can have different qualities (480p, HD) and 
extra features (subtitles) — creating a separate class for every 
combination would lead to an explosion of subclasses.

**Solution:** `BasicVideo` is the base component. `HDDecorator` and 
`SubtitleDecorator` wrap the video and add functionality dynamically. 
Decorators can be combined in any order — each one builds on top 
of the previous description.

---

## How they work together

A video is first built using the Decorator pattern (e.g. Basic → HD → Subtitles),
then its description is passed to the channel's `uploadVideo` method,
which triggers the Observer pattern and notifies all current subscribers.
