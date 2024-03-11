GROUP A
cd voting_system
python manage.py startapp voting
# voting/models.py
from django.db import models

class Student(models.Model):
    name = models.CharField(max_length=100)
    student_id = models.CharField(max_length=20, unique=True)

    def __str__(self):
        return self.name

class Candidate(models.Model):
    name = models.CharField(max_length=100)
    position = models.CharField(max_length=100)

    def __str__(self):
        return self.name

class Vote(models.Model):
    student = models.ForeignKey(Student, on_delete=models.CASCADE)
    candidate = models.ForeignKey(Candidate, on_delete=models.CASCADE)

    def __str__(self):
        return f"{self.student} voted for {self.candidate}"
        # voting/admin.py
from django.contrib import admin
from .models import Student, Candidate, Vote

admin.site.register(Student)
admin.site.register(Candidate)
admin.site.register(Vote)

