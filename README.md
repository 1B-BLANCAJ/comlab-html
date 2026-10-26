# comlab-html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Computer Laboratory Student Attendance Monitoring System</title>
    <link rel="stylesheet" href="style.css">
    <script src="script.js" defer></script>
</head>
<body>

<header>
    <div class="logo">📋</div>
    <div class="brand">
        <h1>Computer Laboratory Student Attendance Monitoring System</h1>
        <p>Student Attendance and Instructor Monitoring System</p>
    </div>
</header>

<nav>
    <button class="active" data-page="student">
        <span class="icon">🧑‍🎓</span>Student Attendance
    </button>
    <button data-page="login">
        <span class="icon">👩‍🏫</span>Instructor Login
    </button>
    <button data-page="dashboard" id="dashNav" hidden>
        <span class="icon">📊</span>Dashboard
    </button>
</nav>

<main>
    <!-- STUDENT ATTENDANCE -->
    <section class="page active" id="student">
        <h2>MARK YOUR ATTENDANCE<br>STUDENTS</h2>

        <form id="attendanceForm">
            <div class="field">
                <label for="sid">Student ID</label>
                <input id="sid" placeholder="Example: 2026-001" required>
            </div>

            <div class="field">
                <label for="sname">Student Name</label>
                <input id="sname" placeholder="Enter your full name" required>
            </div>

            <div class="field">
                <label for="section">Section</label>
                <select id="section" required>
                    <option value="">Select your section</option>
                    <option>BSIT - 1A</option>
                    <option>BSIT - 1B</option>
                    <option>BSIT - 1C</option>
                    <option>BSIT - 1D</option>
                    <option>BSIT - 1E</option>
                </select>
            </div>

            <div class="field">
                <label for="lab">Laboratory</label>
                <select id="lab" required>
                    <option value="">Select laboratory</option>
                    <option>Computer Laboratory 1</option>
                    <option>Computer Laboratory 2</option>
                    <option>Computer Laboratory 3</option>
                </select>
            </div>

            <div class="field">
                <label for="code">Attendance Code</label>
                <input id="code"
                       placeholder="Enter code shown by instructor"
                       inputmode="numeric" required>
            </div>

            <p class="note">
                Ask your instructor for the active attendance code.
                Do not share it with absent students.
            </p>

            <button class="primary" type="submit">
                Confirm Attendance
            </button>

            <div id="attMsg" class="message" role="status"></div>
        </form>
    </section>

    <!-- INSTRUCTOR LOGIN -->
    <section class="page" id="login">
        <div class="loginbox">
            <h2>Instructor Login</h2>

            <form id="loginForm">
                <div class="field">
                    <label for="username">Username</label>
                    <input id="username"
                           placeholder="Enter username"
                           autocomplete="username" required>
                </div>

                <div class="field">
                    <label for="password">Password</label>
                    <input id="password" type="password"
                           placeholder="Enter password"
                           autocomplete="current-password" required>
                </div>

                <button class="primary" type="submit">Login</button>
                <div id="loginMsg" class="message" role="status"></div>

                <p class="note">Demo login: instructor / 1234</p>
            </form>
        </div>
    </section>

    <!-- INSTRUCTOR DASHBOARD -->
    <section class="page" id="dashboard">
        <h2>Instructor Dashboard</h2>

        <div class="panel">
            <h3>Attendance Session</h3>
            <p class="note">
                Start a session, then show the temporary code
                on the laboratory screen.
            </p>

            <div class="stats">
                <div class="stat">
                    <strong id="sessStatus">Closed</strong>
                    <span>Session</span>
                </div>
                <div class="stat">
                    <strong id="sessCode">------</strong>
                    <span>Attendance Code</span>
                </div>
                <div class="stat">
                    <strong id="timer">--</strong>
                    <span>Seconds Left</span>
                </div>
            </div>

            <button class="primary" id="start" type="button">
                Start Attendance (5 minutes)
            </button>

            <p id="sessNote" class="note">
                Demo code expires after 5 minutes.
            </p>
        </div>

        <div class="panel">
            <h3>Recorded Attendance</h3>

            <div class="stats">
                <div class="stat">
                    <strong id="total">0</strong>
                    <span>Total</span>
                </div>
                <div class="stat">
                    <strong id="present">0</strong>
                    <span>Present</span>
                </div>
                <div class="stat">
                    <strong id="late">0</strong>
                    <span>Late</span>
                </div>
            </div>

            <div class="tablewrap">
                <table>
                    <thead>
                        <tr>
                            <th>Student ID</th>
                            <th>Name</th>
                            <th>Section</th>
                            <th>Laboratory</th>
                            <th>Time</th>
                            <th>Status</th>
                        </tr>
                    </thead>
                    <tbody id="rows">
                        <tr>
                            <td colspan="6">
                                No attendance recorded yet.
                            </td>
                        </tr>
                    </tbody>
                </table>
            </div>

            <button class="small" id="clear" type="button">
                Clear Demo Records
            </button>
        </div>

        <button class="primary logout" id="logout" type="button">
            Logout
        </button>
    </section>
</main>

</body>
</html>
