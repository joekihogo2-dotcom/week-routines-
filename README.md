<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">

<meta
  name="viewport"
  content="width=device-width, initial-scale=1.0, viewport-fit=cover"
/>

<meta name="theme-color" content="#08090d">

<meta
  name="apple-mobile-web-app-capable"
  content="yes"
/>

<meta
  name="apple-mobile-web-app-status-bar-style"
  content="black-translucent"
/>

<meta
  name="apple-mobile-web-app-title"
  content="Weekly Routine"
/>

<title>Weekly Routine</title>

<style>

* {
  box-sizing: border-box;
  -webkit-tap-highlight-color: transparent;
}

:root {
  --bg: #08090d;
  --card: #13151b;
  --card2: #191c23;
  --border: #272b35;
  --text: #f5f7fa;
  --muted: #8d95a5;

  --workout: #ff6868;
  --mandarin: #ff8ca8;
  --electronics: #9c7ce5;
  --school: #4dd0c4;
  --tlevel: #4c94ff;
  --flashcards: #a6df62;
  --sleep: #6d63ff;
}

body {
  margin: 0;
  background: var(--bg);
  color: var(--text);
  font-family:
    -apple-system,
    BlinkMacSystemFont,
    "SF Pro Display",
    "Segoe UI",
    sans-serif;
}

button {
  font: inherit;
}

#app {
  max-width: 600px;
  margin: auto;
  min-height: 100vh;
  padding:
    env(safe-area-inset-top)
    16px
    calc(35px + env(safe-area-inset-bottom));
}

/* LOGIN */

#lockScreen {
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 25px;
}

.lockBox {
  width: 100%;
  max-width: 360px;
  text-align: center;
}

.lockIcon {
  font-size: 55px;
  margin-bottom: 20px;
}

.lockBox h1 {
  margin: 0;
  font-size: 30px;
}

.lockBox p {
  color: var(--muted);
  margin-bottom: 25px;
}

.pinInput {
  width: 100%;
  background: var(--card);
  border: 1px solid var(--border);
  color: white;
  padding: 16px;
  border-radius: 16px;
  text-align: center;
  font-size: 22px;
  letter-spacing: 8px;
  outline: none;
}

.unlockButton {
  width: 100%;
  margin-top: 12px;
  padding: 15px;
  border: 0;
  border-radius: 16px;
  background: white;
  color: black;
  font-weight: 800;
}

/* HEADER */

.header {
  padding-top: 18px;
}

.topLine {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.title {
  font-size: 29px;
  font-weight: 850;
  letter-spacing: -1px;
}

.subtitle {
  color: var(--muted);
  font-size: 13px;
  margin-top: 4px;
}

.clock {
  font-size: 16px;
  font-weight: 750;
}

.date {
  color: var(--muted);
  margin-top: 10px;
  font-size: 14px;
}

/* PROGRESS */

.progressCard,
.nextCard,
.notificationCard {
  background: var(--card);
  border: 1px solid var(--border);
  border-radius: 20px;
  padding: 17px;
  margin-top: 16px;
}

.progressTop {
  display: flex;
  justify-content: space-between;
  font-size: 14px;
  font-weight: 700;
}

.progressNumber {
  color: var(--muted);
}

.progressTrack {
  height: 7px;
  background: #22252d;
  border-radius: 20px;
  overflow: hidden;
  margin-top: 13px;
}

.progressBar {
  height: 100%;
  width: 0%;
  background: var(--school);
  border-radius: 20px;
  transition: width .3s ease;
}

/* NEXT */

.nextCard {
  background:
    linear-gradient(
      145deg,
      #191c23,
      #101217
    );
}

.nextLabel {
  color: var(--muted);
  font-size: 10px;
  font-weight: 850;
  letter-spacing: 1.5px;
}

.nextName {
  font-size: 27px;
  font-weight: 850;
  margin-top: 10px;
}

.nextBottom {
  display: flex;
  gap: 10px;
  align-items: center;
  margin-top: 6px;
}

.nextTime {
  font-weight: 800;
}

.countdown {
  color: var(--muted);
}

/* NOTIFICATIONS */

.notificationCard {
  display: flex;
  align-items: center;
  gap: 12px;
}

.notificationIcon {
  font-size: 24px;
}

.notificationText {
  flex: 1;
}

.notificationTitle {
  font-weight: 750;
  font-size: 14px;
}

.notificationDescription {
  color: var(--muted);
  font-size: 11px;
  margin-top: 3px;
}

.notificationButton {
  border: 0;
  background: white;
  color: black;
  border-radius: 12px;
  padding: 9px 12px;
  font-size: 12px;
  font-weight: 800;
}

/* ROUTINE */

.sectionTitle {
  margin-top: 28px;
  margin-bottom: 13px;
  font-size: 20px;
  font-weight: 850;
}

.routine {
  display: flex;
  flex-direction: column;
  gap: 9px;
}

.block {
  display: flex;
  align-items: center;
  background: var(--card);
  border: 1px solid var(--border);
  border-radius: 17px;
  padding: 13px;
  min-height: 70px;
  transition: .2s;
}

.block:active {
  transform: scale(.98);
}

.block.completed {
  opacity: .48;
}

.time {
  width: 65px;
  font-size: 13px;
  font-weight: 800;
}

.until {
  display: block;
  color: var(--muted);
  font-size: 9px;
  margin-top: 3px;
}

.activity {
  flex: 1;
  display: flex;
  align-items: center;
  gap: 10px;
}

.dot {
  width: 5px;
  height: 31px;
  border-radius: 5px;
}

.activityName {
  font-size: 14px;
  font-weight: 750;
}

.checkbox {
  width: 27px;
  height: 27px;
  border: 2px solid var(--border);
  border-radius: 9px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-weight: 900;
}

.completed .checkbox {
  background: var(--school);
  border-color: var(--school);
  color: #08090d;
}

.completed .activityName {
  text-decoration: line-through;
}

/* RESET */

.reset {
  width: 100%;
  margin-top: 18px;
  height: 50px;
  border-radius: 15px;
  background: transparent;
  border: 1px solid var(--border);
  color: var(--muted);
  font-weight: 700;
}

.footer {
  text-align: center;
  color: var(--muted);
  font-size: 10px;
  margin-top: 16px;
}

.hidden {
  display: none !important;
}

</style>
</head>

<body>

<!-- LOCK SCREEN -->

<div id="lockScreen">

  <div class="lockBox">

    <div class="lockIcon">🔐</div>

    <h1>Weekly Routine</h1>

    <p>Your personal routine</p>

    <input
      id="pinInput"
      class="pinInput"
      type="password"
      inputmode="numeric"
      maxlength="6"
      placeholder="••••"
    >

    <button
      class="unlockButton"
      onclick="unlock()"
    >
      Unlock
    </button>

  </div>

</div>


<!-- APP -->

<main id="app" class="hidden">

  <header class="header">

    <div class="topLine">

      <div>

        <div class="title">
          Weekly Routine
        </div>

        <div class="subtitle">
          Stay consistent. One block at a time.
        </div>

      </div>

      <div id="clock" class="clock">
        00:00
      </div>

    </div>

    <div id="date" class="date">
      Loading...
    </div>

  </header>


  <!-- PROGRESS -->

  <section class="progressCard">

    <div class="progressTop">

      <span>
        Today's progress
      </span>

      <span
        id="progressNumber"
        class="progressNumber"
      >
        0/7
      </span>

    </div>

    <div class="progressTrack">

      <div
        id="progressBar"
        class="progressBar"
      ></div>

    </div>

  </section>


  <!-- NEXT -->

  <section class="nextCard">

    <div class="nextLabel">
      NEXT BLOCK
    </div>

    <div
      id="nextName"
      class="nextName"
    >
      Loading...
    </div>

    <div class="nextBottom">

      <span
        id="nextTime"
        class="nextTime"
      >
        --
      </span>

      <span
        id="countdown"
        class="countdown"
      >
        --
      </span>

    </div>

  </section>


  <!-- NOTIFICATIONS -->

  <section
    id="notificationCard"
    class="notificationCard"
  >

    <div class="notificationIcon">
      🔔
    </div>

    <div class="notificationText">

      <div class="notificationTitle">
        Notifications
      </div>

      <div class="notificationDescription">
        Allow this app to send notifications.
      </div>

    </div>

    <button
      class="notificationButton"
      onclick="enableNotifications()"
    >
      Enable
    </button>

  </section>


  <div class="sectionTitle">
    Today's routine
  </div>

  <section
    id="routine"
    class="routine"
  ></section>


  <button
    class="reset"
    onclick="resetDay()"
  >
    ↻ Reset today's ticks
  </button>


  <div class="footer">
    Your progress is saved automatically on this device.
  </div>

</main>


<script>

const PIN = "1234";

const schedule = [
  {
    id: "workout",
    name: "Workout",
    time: "04:30",
    color: "var(--workout)"
  },

  {
    id: "mandarin",
    name: "Mandarin",
    time: "05:30",
    color: "var(--mandarin)"
  },

  {
    id: "electronics",
    name: "Electronics",
    time: "06:30",
    color: "var(--electronics)"
  },

  {
    id: "school",
    name: "School",
    time: "08:25",
    end: "11:30",
    color: "var(--school)"
  },

  {
    id: "tlevel",
    name: "T Level / Projects",
    time: "11:30",
    color: "var(--tlevel)"
  },

  {
    id: "flashcards",
    name: "Flashcards / Review",
    time: "19:00",
    color: "var(--flashcards)"
  },

  {
    id: "sleep",
    name: "Sleep",
    time: "22:30",
    color: "var(--sleep)"
  }
];


function dateKey() {

  const d = new Date();

  return d.getFullYear()
    + "-"
    + String(d.getMonth() + 1).padStart(2, "0")
    + "-"
    + String(d.getDate()).padStart(2, "0");

}


function storageKey() {

  return "routine-" + dateKey();

}


function unlock() {

  const input =
    document.getElementById("pinInput").value;

  if (input === PIN) {

    localStorage.setItem(
      "routineUnlocked",
      "true"
    );

    showApp();

  } else {

    alert("Incorrect PIN.");

  }

}


function showApp() {

  document
    .getElementById("lockScreen")
    .classList.add("hidden");

  document
    .getElementById("app")
    .classList.remove("hidden");

  render();

}


function getTicks() {

  return JSON.parse(
    localStorage.getItem(storageKey())
    || "{}"
  );

}


function saveTicks(ticks) {

  localStorage.setItem(
    storageKey(),
    JSON.stringify(ticks)
  );

}


function toggle(id) {

  const ticks = getTicks();

  ticks[id] = !ticks[id];

  saveTicks(ticks);

  render();

}


function resetDay() {

  if (
    confirm(
      "Reset all ticks for today?"
    )
  ) {

    localStorage.removeItem(
      storageKey()
    );

    render();

  }

}


function minutes(time) {

  const parts = time
    .split(":")
    .map(Number);

  return parts[0] * 60 + parts[1];

}


function getNextBlock() {

  const now = new Date();

  const current =
    now.getHours() * 60
    + now.getMinutes();

  return schedule.find(
    item => minutes(item.time) > current
  );

}


function updateClock() {

  const now = new Date();

  document.getElementById("clock")
    .textContent =
    now.toLocaleTimeString([], {
      hour: "2-digit",
      minute: "2-digit"
    });

  document.getElementById("date")
    .textContent =
    now.toLocaleDateString([], {
      weekday: "long",
      day: "numeric",
      month: "long"
    });

  updateNext();

}


function updateNext() {

  const next = getNextBlock();

  if (!next) {

    document.getElementById("nextName")
      .textContent =
      "Routine complete 🎉";

    document.getElementById("nextTime")
      .textContent = "";

    document.getElementById("countdown")
      .textContent = "";

    return;

  }

  const now = new Date();

  const current =
    now.getHours() * 60
    + now.getMinutes();

  const difference =
    minutes(next.time) - current;

  const hours =
    Math.floor(difference / 60);

  const mins =
    difference % 60;

  let text = "";

  if (hours > 0) {

    text =
      `in ${hours}h ${mins}m`;

  } else {

    text =
      `in ${mins}m`;

  }

  document.getElementById("nextName")
    .textContent = next.name;

  document.getElementById("nextTime")
    .textContent = next.time;

  document.getElementById("countdown")
    .textContent = text;

}


function render() {

  const ticks = getTicks();

  const routine =
    document.getElementById("routine");

  routine.innerHTML = "";

  let completed = 0;

  schedule.forEach(item => {

    const done = ticks[item.id];

    if (done) completed++;

    const block =
      document.createElement("button");

    block.className =
      "block"
      + (done ? " completed" : "");

    block.style.width = "100%";
    block.style.textAlign = "left";
    block.style.color = "inherit";

    block.onclick =
      () => toggle(item.id);

    block.innerHTML = `

      <div class="time">

        ${item.time}

        ${
          item.end
            ? `<span class="until">
                until ${item.end}
              </span>`
            : ""
        }

      </div>

      <div class="activity">

        <div
          class="dot"
          style="background:${item.color}"
        ></div>

        <div class="activityName">
          ${item.name}
        </div>

      </div>

      <div class="checkbox">

        ${done ? "✓" : ""}

      </div>

    `;

    routine.appendChild(block);

  });


  const percentage =
    (completed / schedule.length) * 100;

  document.getElementById(
    "progressNumber"
  ).textContent =
    `${completed}/${schedule.length}`;

  document.getElementById(
    "progressBar"
  ).style.width =
    percentage + "%";

  updateNext();

}


async function enableNotifications() {

  if (!("Notification" in window)) {

    alert(
      "Notifications aren't supported here."
    );

    return;

  }

  const permission =
    await Notification.requestPermission();

  if (permission === "granted") {

    new Notification(
      "Weekly Routine",
      {
        body:
          "Notifications are enabled."
      }
    );

    document
      .getElementById(
        "notificationCard"
      )
      .innerHTML = `

        <div class="notificationIcon">
          ✅
        </div>

        <div class="notificationText">

          <div class="notificationTitle">
            Notifications enabled
          </div>

          <div class="notificationDescription">
            iPhone notifications are active.
          </div>

        </div>

      `;

  }

}


/*
   Keep clock updated.
*/

setInterval(
  updateClock,
  1000
);


/*
   Automatically show app if unlocked.
*/

if (
  localStorage.getItem(
    "routineUnlocked"
  ) === "true"
) {

  showApp();

} else {

  document
    .getElementById(
      "lockScreen"
    )
    .classList.remove("hidden");

}


/*
   Initial clock.
*/

updateClock();

</script>

</body>
</html>
