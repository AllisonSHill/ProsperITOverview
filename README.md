# Live Project

## Intro:

At the end of my time at the Tech Academy, I spent six weeks working with a team of fellow students to develop a full scale MVC/MVVM Web Application in C#. It was structured in two week sprints, during which I focused on both Front-End and Back-End development stories. 

## Front End Stories:

### Create ShiftTime Modal

The first story was the front-end development of a modal on the Job Creation page to add shift times to new jobs as they were created. The request was for the addition of a button in the existing Job Create form, in place of an existing text box to add shift times, that would launch a ShiftTime Modal. The modal wanted to contain a series of text boxes for a default shift time, as well as the ability to enter alternate shift times for every day of the week. The story specifically stated that the modal be a separate partial view, within the Jobs folder. After I completed this story, I took a back end story /Link this here/ for the initial implementation of the modal's functionality. 

```
@model ManagementPortal.Models.ShiftTime

@{
    ViewBag.Title = "Create";
}

<div id="ShiftTimeModal" class="modal fade hidden-print" tabindex="-1" role="dialog">
    <div class="modal-dialog modalShiftTimes" role="document">
        <div class="modal-content">
            <div class="modal-header">
                <button type="button" class="close" data-dismiss="modal" aria-label="Close">
                    <span aria-hidden="true">&times;</span>
                </button>
                <h4 class="modal-title">Modify Shift Times</h4>
            </div>
            <div class="modal-body">
                <div id="formContent">
                    @using (Html.BeginForm("Create", "ShiftTimes", FormMethod.Post, new { id = "form-shiftTimeAdd" }))
                    {
                        <div class="form-horizontal">
                            <div class="form-group">
                                @Html.LabelFor(model => model.Default, htmlAttributes: new { @class = "control-label col-md-2" })
                                <div class="col-md-6">
                                    @Html.EditorFor(model => model.Default, new { htmlAttributes = new { @class = "form-control" } })
                                    @Html.ValidationMessageFor(model => model.Default, "", new { @class = "text-danger" })
                                </div>
                            </div>
                            @Html.ValidationSummary(true, "", new { @class = "text-danger" })
                            <div class="form-group">
                                @Html.LabelFor(model => model.Monday, htmlAttributes: new { @class = "control-label col-md-2" })
                                <div class="col-md-6">
                                    @Html.EditorFor(model => model.Monday, new { htmlAttributes = new { @class = "form-control" } })
                                    @Html.ValidationMessageFor(model => model.Monday, "", new { @class = "text-danger" })
                                </div>
                            </div>
                            @Html.ValidationSummary(true, "", new { @class = "text-danger" })
                            <div class="form-group">
                                @Html.LabelFor(model => model.Tuesday, htmlAttributes: new { @class = "control-label col-md-2" })
                                <div class="col-md-6">
                                    @Html.EditorFor(model => model.Tuesday, new { htmlAttributes = new { @class = "form-control" } })
                                    @Html.ValidationMessageFor(model => model.Tuesday, "", new { @class = "text-danger" })
                                </div>
                            </div>
                            @Html.ValidationSummary(true, "", new { @class = "text-danger" })
                            <div class="form-group">
                                @Html.LabelFor(model => model.Wednesday, htmlAttributes: new { @class = "control-label col-md-2" })
                                <div class="col-md-6">
                                    @Html.EditorFor(model => model.Wednesday, new { htmlAttributes = new { @class = "form-control" } })
                                    @Html.ValidationMessageFor(model => model.Wednesday, "", new { @class = "text-danger" })
                                </div>
                            </div>
                            @Html.ValidationSummary(true, "", new { @class = "text-danger" })
                            <div class="form-group">
                                @Html.LabelFor(model => model.Thursday, htmlAttributes: new { @class = "control-label col-md-2" })
                                <div class="col-md-6">
                                    @Html.EditorFor(model => model.Thursday, new { htmlAttributes = new { @class = "form-control" } })
                                    @Html.ValidationMessageFor(model => model.Thursday, "", new { @class = "text-danger" })
                                </div>
                            </div>
                            @Html.ValidationSummary(true, "", new { @class = "text-danger" })
                            <div class="form-group">
                                @Html.LabelFor(model => model.Friday, htmlAttributes: new { @class = "control-label col-md-2" })
                                <div class="col-md-6">
                                    @Html.EditorFor(model => model.Friday, new { htmlAttributes = new { @class = "form-control" } })
                                    @Html.ValidationMessageFor(model => model.Friday, "", new { @class = "text-danger" })
                                </div>
                            </div>
                            @Html.ValidationSummary(true, "", new { @class = "text-danger" })
                            <div class="form-group">
                                @Html.LabelFor(model => model.Saturday, htmlAttributes: new { @class = "control-label col-md-2" })
                                <div class="col-md-6">
                                    @Html.EditorFor(model => model.Saturday, new { htmlAttributes = new { @class = "form-control" } })
                                    @Html.ValidationMessageFor(model => model.Saturday, "", new { @class = "text-danger" })
                                </div>
                            </div>
                            @Html.ValidationSummary(true, "", new { @class = "text-danger" })
                            <div class="form-group">
                                @Html.LabelFor(model => model.Sunday, htmlAttributes: new { @class = "control-label col-md-2" })
                                <div class="col-md-6">
                                    @Html.EditorFor(model => model.Sunday, new { htmlAttributes = new { @class = "form-control" } })
                                    @Html.ValidationMessageFor(model => model.Sunday, "", new { @class = "text-danger" })
                                </div>
                            </div>
                        </div>

                        <button type="button" class="btn btn-default" data-dismiss="modal">Close</button>
                    }
                </div>
            </div>
        </div>
    </div>
</div>
```

### Chat Box Upgrade

The third story I worked on was upgrading the site's chat feature. The chat feature was already set up to open on all logged in user's screens when a message was sent, as well as save the messages in a database and populate old messages every time the Chat Modal was launched. I created chat bubbles based on a sample image I was given. 

//screenshot of sample image

```
.chatBubbles {
    border-radius: 20px;
    padding: 8px 15px;
    display: inline-block;
    background-attachment: fixed;
    position: relative;
}

#myChat {
    text-align: right;
    color: white;
    margin-top: 0px;
    margin-bottom: 4px;
    background: grey;
    margin-right: 8%;
    margin-left: 25%;
    float: right;
}

#myChat::before {
    content: "";
    position: absolute;
    z-index: 0;
    bottom: 0;
    right: -8px;
    height: 20px;
    width: 20px;
    background: grey;
    background-attachment: fixed;
    border-bottom-left-radius: 15px;
}

#myChat::after {
    content: "";
    position: absolute;
    z-index: 1;
    bottom: 0;
    right: -10px;
    width: 10px;
    height: 20px;
    background: white;
    border-bottom-left-radius: 10px;
}

#yourChat {
    text-align: left;
    color: black;
    margin-top: 10px;
    margin-bottom: -5px;
    background: #DADADA;
    margin-left: 8%;
    margin-right: 25%;
}

#yourChat::before{
    content: "";
    position: absolute;
    z-index: 0;
    bottom: 0;
    left: -7px;
    height: 20px;
    width: 20px;
    background: #DADADA;
    border-bottom-right-radius: 15px;
}

#yourChat::after {
    content: "";
    position: absolute;
    z-index: 1;
    bottom: 0;
    left: -10px;
    width: 10px;
    height: 20px;
    background: white;
    border-bottom-right-radius: 10px;
}

#myName {
    text-align: right;
    float: right;
    margin-top: -10px;
    margin-bottom: -4px;
}

#yourName {
    text-align: left;
    margin-top: -20px;
}
```

For bonus functionality, I added script to allow new chat messages to be sent by hitting the enter key, and I changed the direction the message populated and scrolled to be more intuitive. 

```
//use enter key to send new chat message
$("#message-box").keyup(function (e) {
    if (e.keyCode === 13) {
        $("#send-message").click();
    }
});
```
```
//populates messages from database into messenger on startup
chat.client.populateMessages = function (messageList, me) {
    for (var message in messageList) {
        var userName = messageList[message]['UserName'];
        if (userName == me) {
            $('#discussion').prepend('<li><div id="myChat" class="chatBubbles">' + messageList[message]['Message'] + '</div></li><br><br><div id="myName"><sub>' + messageList[message]['UserName'] + '</sub ></div><br>');
        }
        else {
            $('#discussion').prepend('<li><div id="yourChat" class="chatBubbles">' + messageList[message]['Message'] + '</div></li><sub>' + messageList[message]['UserName'] + '</sub >');
            continue;
        }
    }
};  
```
```
//prints newly sent instant message to everyones messenger
chat.client.receiveMessage = function (userName, me, message) {
    if (userName == me) {
        $('#discussion').append('<li><div id="myChat" class="chatBubbles">' + message + '</div></li><br><br><div id="myName"><sub>' + userName + '</sub></div><br>');
    }
    else {
        $('#discussion').append('<li><div id="yourChat" class="chatBubbles">' + message + '</div></li><sub>' + userName + '</sub>');
    }
    $('#discussion').animate({
        scrollTop: $('#discussion').get(0).scrollHeight
    }, 800);
};
```

The most challenging part of this story was figuring out how to change the styling of the chat bubbles based on the currently logged in user, so the user would see their chat messages on the right of the module, and a different color than everyone else's chat. The solution ended up being very simple:  

```
string me = Context.User.Identity.Name;
```

//screenshot of final chat view

## Back End Stories:

### Implement ShiftTime Modal

The goal of this story was to write a function for the ShiftTime Modal to save a ShiftTime object and match it with a job that is being created. There was a note in the story that there would be a follow up story to link the ShiftTime to the correct Job in the database. I accomplished this task by adding to the Create function within the JobsController, using a bind statement to submit the data from the ShiftTime Modal through clicking the Submit button of the parent Add Job form. 

```
// POST: Jobs/Create
[HttpPost]
[ValidateAntiForgeryToken]
public ActionResult Create([Bind(Include = "JobIb,JobTitle,JobType,Active,Location,Manager")] Job job,
    [Bind(Include = "ShiftTimeId,Monday,Tuesday,Wednesday,Thursday,Friday,Saturday,Sunday,Default")] ShiftTime shiftTime)
{
    shiftTime.Job = job;
    PopulateJobDropDowns(job);
    var LocationId = Request.Form["LocationSelector"].ToString();
    var ManagerId = Request.Form["ManagerSelector"].ToString();
    if (ModelState.IsValid)
    {
        job.Location = db.JobSites.Find(Int32.Parse(LocationId));
        job.Manager = db.Users.Find(ManagerId);
        db.Jobs.Add(job);
        db.ShiftTime.Add(shiftTime);
        db.SaveChanges();
        return RedirectToAction("Index");
    }
 ```

### Job to Schedules Function

From story: We will want to be able to display the schedule items sorted by job. To allow for future functionality to filter these by person or by date, etc, We need a function that takes a specific list of schedule items and builds a dictionary item where the key is the job and the value is the list of schedules for that job. 

```
//Job to schedules dictionary function
private Dictionary<Job, List<Schedule>> AddToDictionary(List<Schedule> schedules)
{
    var scheduleDict = new Dictionary<Job, List<Schedule>>();
    foreach (var schedule in schedules)
    {
        var schedJob = schedule.Job;
        if (scheduleDict.ContainsKey(schedJob))
            {
            scheduleDict[schedule.Job].Add(schedule);
            }
        else
            {
            var assignedSchedules = new List<Schedule>();
            assignedSchedules.Add(schedule);
            scheduleDict.Add(schedJob, assignedSchedules);
            }
        }
    return scheduleDict;
}
```

### Back End: Calendar Pull Existing Schedule

From story: The calendar allows for people to set their schedule for time off, but we want it to also populate the events currently scheduled. Create a method within the Calendar Controller that will check for existing schedule items and add them to the calendar. 

```
[HttpGet]
public void ShowScheduleItems()
{
    var schedules = db.Schedules.ToList();
    foreach (var schedule in schedules)
    {
        var schEvent = new CalendarEvent();
        //convert schedule event properties into calendar event properties
        schEvent.Subject = Convert.ToString(schedule.Job.JobTitle);
        schEvent.Start = schedule.StartDate;
        schEvent.End = schedule.EndDate;
        schEvent.Description = "Employee: " + Convert.ToString(schedule.Person.DisplayName) + "  " + "\nJob Type: " + Convert.ToString(schedule.Job.JobType);
        schEvent.IsFullDay = true;
        schEvent.ScheduleId = Convert.ToString(schedule.ScheduleId);
        if (schEvent.End > DateTime.Now.Date && schEvent.Start < DateTime.Now.Date)
        {
            schEvent.Start = DateTime.Now.AddMinutes(1);
        }
        try
        {
            if (ModelState.IsValid)
            {
                //check if an event with a matching ScheduleId is currently on the calendar
                var match = db.CalendarEvents.Where(a => a.ScheduleId == schEvent.ScheduleId).SingleOrDefault();
                if (match != null)
                {
                    var oldSchEvent = match;
                    //check for differences in any properties between events with matching ScheduleId and update db
                    if (oldSchEvent.Subject != schEvent.Subject)
                    {
                        oldSchEvent.Subject = schEvent.Subject;
                    }
                    else if (oldSchEvent.Start != schEvent.Start)
                    {
                        oldSchEvent.Start = schEvent.Start;
                    }
                    else if (oldSchEvent.End != schEvent.End)
                    {
                        oldSchEvent.End = schEvent.End;
                    }
                    else if (oldSchEvent.Description != schEvent.Description)
                    {
                        oldSchEvent.Description = schEvent.Description;
                    }
                    else if (oldSchEvent.IsFullDay != schEvent.IsFullDay)
                    {
                        oldSchEvent.IsFullDay = schEvent.IsFullDay;
                    }
                    else
                    {
                        continue;
                    }
                    //update database entry
                    db.Entry(oldSchEvent).State = EntityState.Modified;
                    db.SaveChanges();
                }
                else //add new event
                {
                    db.CalendarEvents.Add(schEvent);
                    db.SaveChanges();
                }
            }
        }
        catch
        {
            throw new ArgumentException("Event cannot end before today's date.");
        }
    }
}
```

### User-Role Assignment Must Be Required and Save Changes Minor Bug

From stories: 
When the Admin creates a new user (on CreateUserRequest/Create)
there is a drop down option to assign the new user a "Role". This must be a required field and the Admin shouldn't be allowed to create a new user  (submit the page) without a role. 

```
[Required]
[Display(Name = "User Role")]
public string UserRole { get; set; }
```
Then it was as simple as adding one line to the "Create New User" view:
```
@Html.ValidationMessageFor(model => model.UserRole, "", new { @class = "text-danger" })
```

In Manage/EditAccountInfo view page, the save changes button is serving its purpose by saving the changes. But more than that, it should also take the user back Mange/Index page or (Home/Dashboard) when clicked. All I had to do was one minor edit on the Manage Controller/EditAccountInfo function, which was triggered by the save changes button. 

```
return RedirectToAction("Index", "Manage");
```

Each of these stories needed only one line of code to complete them, so I finished them up quickly. 

### User Manager Clean Up

I chose to work on a story that addressed four separate bugs in the User Manager. This was a board where the site Admin could update user roles and delete users. 

From story:
1) There is sometimes an error message stating that a user is already in a role they are being assigned to. This means that we are not unassigning the old role when changing the role. Add logic to the back end to unassign the user from the previous role before assigning them to the new role.

```
function updateUserRole(formId) {
var form = $('#roleForm_' + formId);
if (confirm("Warning: Are you sure you want to change this user's role? ")) {
    $.ajax({
        url: form.attr("action"),
        type: form.attr("method"),
        data: form.serialize(),
        datatype: "application/json",
        success: function (returnJson) {
            if (returnJson.result == "success") {
                alert("Success! " + returnJson.displayName + " is now a " + returnJson.newRole);
            }
            else if (returnJson.result == "error") {
                alert("Error: " + returnJson.message); 
            }
            else if (returnJson.result == "warning") {
                alert("Warning: " + returnJson.warning);
            }
            else if (returnJson.result == "message") {
                alert("Error: " + returnJson.message);
                location.reload();
            }
        },
        error: function () {
            alert("Error: invalid ajax request");
        }
    });
}
else {
    return false;
}
}
```

2) The error message for not deleting someone from the database who is on the schedule displays the users GUID instead of their name when alerting the admin they cannot delete this user. Change this to be the user's display name.

```
I passed in the displayname to the javascript function. I think. This whole section is messy af I have to figure it out. 
```

3) The message asking if the admin is sure they want to delete a user displays the username. Change this to the display name.



4) There should be a cancel option for assigning the role or deleting the user. Make sure there are two buttons on the pop-up message, one for OK and one for Cancel. The cancel one should use a cancel function that does not complete the action.

While working on this story, I ran into some issues that revelealed to the PM that the UserController needed to be refactored. A separate story was created for this, and I took that too because I was familiar with the errors that were currently happening. 

### Refactor User Controller

From story: 
1) Refactor the _UserList method so it grabs the list of users from the database, and sends that list as the model instead of going through what was the process of creating a UserVM. 
2) Exclude the UserVM from the project, test to make sure nothing is dependent on it. Remove any dependencies you find, and delete the User VM.
3) Determine what if anything the Index Users view is doing, and modify it to simply display a list of all users.
4) Determine what if anything the isAdminUser is doing. Replace it with the built in Identity method of checking roles.
5) Add comments to the Users Controller documenting the functions and their purpose, and where they are used.
```c#
using ManagementPortal.Models;
using Microsoft.AspNet.Identity;
using Microsoft.AspNet.Identity.EntityFramework;
using System.Linq;
using System.Web.Mvc;

namespace ManagementPortal.Controllers
{
    public class UsersController : ApplicationBaseController
    {
        private readonly ApplicationDbContext db = new ApplicationDbContext();

        //Display Users/Index view if logged in user is Admin
        [HttpGet]
        [Authorize(Roles = "Admin")]
        public ActionResult Index()
        {
            var model = db.Users.ToList();
            return View("Index", model);
        }

        //Display _UserList on dashboard if logged in user is Admin
        [ChildActionOnly]
        [Authorize(Roles = "Admin")] 
        public ActionResult _UserList()
        {
            var model = db.Users.ToList(); 
            return PartialView("_UserList", model); 
        }

        //Update user role in database from _UserList
        [HttpPost]
        [ValidateAntiForgeryToken]
        [Authorize(Roles = "Admin")]
        public ActionResult UpdateUserRole(string userId, string userRole) //called with "Update" button from _UserList view
        {
           
            if (!string.IsNullOrEmpty(userId) && !string.IsNullOrEmpty(userRole)) //check for required parameters
            {
                if (User.Identity.GetUserId() == userId) //check if current user ID matches ID of user role being changed, return error if true
                {
                    return Json(new { result = "message", message = "You cannot change your own role" });
                }
                else
                {
                    var userManager = new UserManager<ApplicationUser>(new UserStore<ApplicationUser>(db));
                    var user = userManager.FindById(userId); //get user from database
                    if (user != null) //check if requested user exists
                    {
                        if (user.UserRole != userRole) //check if user is already assigned to role they are being switched to
                        {
                            var oldRole = user.UserRole;
                            if (userManager.IsInRole(user.Id, oldRole)) //remove old role from user in db
                            {
                                userManager.RemoveFromRole(user.Id, oldRole);
                            }
                            user.UserRole = userRole; //update variable userRole to new role
                            userManager.AddToRole(user.Id, userRole); //add new role to user in db
                            db.SaveChanges();
                            return Json(new { result = "success", displayName = user.DisplayName, oldRole = oldRole, newRole = userRole }); //send variables to js function for success message
                        }

                        else //return error if user is already assigned to role they are being switched to
                        {
                            return Json(new { result = "error", message = $"user was already in role: {userRole}" });
                        }
                    }
                    else //return error if requested user isn't in database
                    {
                        return Json(new { result = "error", message = $"user id {userId} could not be found in the database" });
                    }
                }
                
            }
            else //return error if userId or userRole is empty for selected user
            {
                return Json(new { result = "error", message = "missing required arguments" });
            }
        }

        //Remove user from database from _UserList
        [HttpPost]
        [ValidateAntiForgeryToken]
        [Authorize(Roles = "Admin")]
        public ActionResult RemoveUser(string userId) //called with "Remove User" button in _UserList
        {
            if (User.Identity.GetUserId() == userId) //check if current user ID matches ID of user being removed, return error if true
            {
                return Json(new { result = "error", message = "you cannot delete yourself" });
            }
            else
            {
                if (!string.IsNullOrEmpty(userId)) //check for ID of user being removed
                {
                    var userManager = new UserManager<ApplicationUser>(new UserStore<ApplicationUser>(db));
                    var user = userManager.FindById(userId); //get user from database
                    if (user != null) //check if user being removed exists in database
                    {
                        var logins = user.Logins; //get login info for user being removed
                        var rolesForUser = userManager.GetRoles(userId); //get role for user being removed
                        using (var transaction = db.Database.BeginTransaction()) //open db connection
                        {
                            var schedules = (from s in db.Schedules //fetch list of users schedules
                                             where s.Person.Id == user.Id
                                             select s).ToList();
                            if (user.Schedules.Count > 0) //check if user is on schedule, return error if true
                            {
                                return Json(new { result = "error", message = $"User {user.DisplayName} is on schedule and could not be deleted." });
                            }
                            foreach (var login in logins.ToList()) //remove login info for user being removed
                                {
                                    userManager.RemoveLogin(login.UserId, new UserLoginInfo(login.LoginProvider, login.ProviderKey));
                                }
                            foreach (var role in rolesForUser.ToList()) //unassign user being removed from role
                                {
                                    userManager.RemoveFromRole(userId, role);
                                }
                                userManager.Delete(user); //delete user from db
                                transaction.Commit();
                                return Json(new { result = "success" });
                        }
                    }
                    else //return error is user being removed is not in db
                    {
                        return Json(new { result = "error", message = $"User {user.DisplayName} could not be found in the database" });
                    }
                }
                else //return error if user ID of user being removed not found
                {
                    return Json(new { result = "error", message = "missing required arguments" });
                }
            }   
        }

        protected override void Dispose(bool disposing)
        {
            if (disposing)
            {
                db.Dispose();
            }
            base.Dispose(disposing);
        }
    }
}
```
