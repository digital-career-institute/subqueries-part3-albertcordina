CREATE TABLE JobOpening (
    JobID INT UNIQUE,
    JobTitle VARCHAR(255),
    Department VARCHAR(255),
    MinimumExperienceYears INT,
    MinimumEducation VARCHAR(255)
);

CREATE TABLE Applicants (
    ApplicantID INT UNIQUE,
    ApplicantName VARCHAR(255),
    ExperienceYears INT,
    Education VARCHAR(255),
    AppliedForJobID INT,
    FOREIGN KEY (AppliedForJobID) REFERENCES JobOpening(JobID)
);	

INSERT INTO JobOpening (JobID, JobTitle, Department, MinimumExperienceYears, MinimumEducation) VALUES
    (101, 'Spacecraft Pilot', 'Flight Operations', 5, 'Bachelor in Aerospace Engineering'),
    (102, 'Mission Specialist', 'Science', 3, 'PhD in Physics or related field'),
    (103, 'Space Engineer', 'Engineering', 3, 'Bachelor in Mechanical Engineering'),
    (104, 'Communication Officer', 'Communications', 2, 'Bachelor in Communication');

						 
INSERT INTO Applicants (ApplicantID, ApplicantName, ExperienceYears, Education, AppliedForJobID) VALUES
    (501, 'John Astronaut', 7, 'Master in Aerospace Engineering', 101),
    (502, 'Lisa Scientist', 4, 'PhD in Physics', 102),
    (503, 'Mark Engineer', 5, 'Bachelor in Mechanical Engineering', 103),
	(504, 'Anna Lulies', 5, 'Bachelor in Mechanical Engineering', NULL),
    (505, 'Jane Communication Specialist', 3, 'Bachelor in Communication', 104);


-- Retrieve a list of all available job openings, including details about the title, department, minimum experience, and minimum education.
SELECT * FROM JobOpening;

-- Display the names of applicants and the jobs they have applied for. Include all applicants, even if they haven't applied for any job.
SELECT A.ApplicantName, J.JobTitle
FROM Applicants A
LEFT JOIN JobOpening J ON A.AppliedForJobID = J.JobID;

-- Create a report showing the names of applicants who meet or exceed the minimum experience and education requirements for the jobs they have applied for.
SELECT A.ApplicantName, J.JobTitle
FROM Applicants A
JOIN JobOpening J ON A.AppliedForJobID = J.JobID
WHERE A.ExperienceYears >= J.MinimumExperienceYears AND A.Education >= J.MinimumEducation;

-- Identify applicants who have applied for a job that currently has no opening.
SELECT A.ApplicantName, A.AppliedForJobID
FROM Applicants A
LEFT JOIN JobOpening J ON A.AppliedForJobID = J.JobID
WHERE J.JobID IS NULL;

-- Find all job openings that require a minimum of 3 to 5 years of experience.
SELECT *
FROM JobOpening
WHERE MinimumExperienceYears BETWEEN 3 AND 5;

-- Retrieve a list of job titles and the count of applicants who have applied for each job, grouped by education level (e.g., Bachelor's, Master's, PhD).
SELECT J.JobTitle, A.Education, COUNT(*) AS ApplicantCount
FROM JobOpening J
LEFT JOIN Applicants A ON J.JobID = A.AppliedForJobID
GROUP BY J.JobTitle, A.Education;
