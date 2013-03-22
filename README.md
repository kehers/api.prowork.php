api.prowork.php
===============

PHP wrapper for the Prowork API at [dev.prowork.me](http://dev.prowork.me/). Take a minute to [read the introduction](http://dev.prowork.me/introduction) and get an API key at [prowork.me/apps](http://prowork.me/apps).

Usage
=====

Sample usage. Login a user and list his projects

	require 'prowork.class.php';
	
	$prowork = new Prowork($apikey);
	if ($prowork->login('fickledreams@yahoo.com', 'take.a.guess')) {
		// Logged in, list my projects
		$projects = $prowork->getProjects();
		
		echo "<ol>";
		foreach ($projects as $project) {
			echo "<li>{$project['name']} &mdash; {$project['member_count']} members, {$project['task_count']} tasks</li>";
		}
		echo "</ol>";
	}
	else {
		// Login failed. Why?
		echo $prowork->getError();
	}
	
Public Methods
==============
Helpers
* getToken
* setToken
* getError
* getAvatar(size, email)

Auth/Notification
* login(email, password)
* register(email, password)
* notificationCount
* activities(read)

Projects
* getProjects
* getProject(project_id)
* newProject(title, description)
* projectActivities(project_id, read)
* deleteProject(project_id)

Project Members
* addProjectMembers(project_id, [array] emails)
* getProjectMembers(project_id)
* removeProjectMember(project_id, member_id)

Tasks
* getTasks(project_id)
* getTask(project_id, task_id)
* newTask(project_id, title, date)
* deleteTask(project_id, task_id)
* setTaskStatus(project_id, task_id, done)

Tasks Members
* assignMembers(project_id, task_id, [array] member_ids)
* removeTaskMember(project_id, task_id, member_id)

I will be working on and adding more methods as necessary. If you need any or have issues with any, don't forget to [hit me up](http://twitter.com/kehers).