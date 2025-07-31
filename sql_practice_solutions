# 🧠 SQL Practice Solutions from sql-practice.com
I completed a series of SQL problems from [sql-practice.com](https://sql-practice.com/) to sharpen my database querying skills.
This includes queries across different difficulty levels, covering SELECT, JOINs, subqueries, string and date functions, and more!

## 🔍 Highlights
- ✅ Solved multiple questions with optimal and alternate solutions.
- 💡 In some cases, I added **multiple query variations** to demonstrate different approaches.
- 📊 A great way to strengthen logical thinking in SQL and improve versatility.

## 🧾 Problem Set

### Question 1 - *Easy*
**Question:** Show first name, last name, and gender of patients whose gender is 'M'

```sql
SELECT 
	first_name, last_name, gender
FROM patients
where gender = "M"
```

### Question 2 - *Easy*
**Question:** Show first name and last name of patients who does not have allergies. (null)

```sql
select first_name, last_name
from patients
where allergies is null
```

### Question 3 - *Easy*
**Question:** Show first name of patients that start with the letter 'C'

```sql
select first_name
from patients
where first_name like "C%"
```

### Question 4 - *Easy*
**Question:** Show first name and last name of patients that weight within the range of 100 to 120 (inclusive)

```sql
select first_name, last_name
from patients
where weight between 100 and 120
```

### Question 5 - *Easy*
**Question:** Update the patients table for the allergies column. If the patient's allergies is null then replace it with 'NKA'

```sql
update patients 
set allergies = "NKA"
where allergies is null
```

### Question 6 - *Easy*
**Question:** Show first name and last name concatinated into one column to show their full name.

```sql
select concat(first_name," ", last_name)
from patients
```

### Question 7 - *Easy*
**Question:** Show first name, last name, and the full province name of each patient.

Example: 'Ontario' instead of 'ON'

```sql
select first_name, last_name, province_name
from patients
join province_names
on patients.province_id=province_names.province_id
```

### Question 8 - *Easy*
**Question:** Show how many patients have a birth_date with 2010 as the birth year.

```sql
select count(*)
from patients
where birth_date like "2010%"
```

### Question 9 - *Easy*
**Question:** Show the first_name, last_name, and height of the patient with the greatest height.

```sql
SELECT
  first_name,
  last_name,
  height
FROM patients
WHERE height = (
    SELECT max(height)
    FROM patients
  )
```

### Question 10 - *Easy*
**Question:** Show all columns for patients who have one of the following patient_ids:
1,45,534,879,1000

```sql
select *
from patients
where patient_id in (1,45,534,879,1000)
```

### Question 11 - *Easy*
**Question:** Show the total number of admissions

```sql
select count(*)
from admissions
```

### Question 12 - *Easy*
**Question:** Show all the columns from admissions where the patient was admitted and discharged on the same day.

```sql
select *
from admissions
where discharge_date = admission_date
```

### Question 13 - *Easy*
**Question:** Show the patient id and the total number of admissions for patient_id 579.

```sql
select patient_id, count(*)
from admissions
where patient_id = 579
```

### Question 14 - *Easy*
**Question:** Based on the cities that our patients live in, show unique cities that are in province_id 'NS'.

```sql
select distinct city
from patients
where province_id = "NS"
```

### Question 15 - *Easy*
**Question:** Write a query to find the first_name, last name and birth date of patients who has height greater than 160 and weight greater than 70

```sql
select first_name, last_name, birth_date
from patients
where height > 160 and weight > 70
```

### Question 16 - *Easy*
**Question:** Write a query to find list of patients first_name, last_name, and allergies where allergies are not null and are from the city of 'Hamilton'

```sql
select first_name, last_name, allergies
from patients
where allergies not null and city = "Hamilton"
```

### Question 17 - *Medium*
**Question:** Show unique birth years from patients and order them by ascending.

```sql
select distinct year(birth_date)
from patients
order by 1 asc
```

### Question 18 - *Medium*
**Question:** Show unique first names from the patients table which only occurs once in the list.

For example, if two or more people are named 'John' in the first_name column then don't include their name in the output list. If only 1 person is named 'Leo' then include them in the output.

```sql
with cte1 as (
select first_name, count(*) as occurrencies
from patients
group by first_name
having occurrencies = 1)
select first_name
from cte1
```

### Question 19 - *Medium*
**Question:** Show patient_id and first_name from patients where their first_name start and ends with 's' and is at least 6 characters long.

```sql
select patient_id, first_name
from patients
where first_name like "S%" and first_name like "%S" and len(first_name) >= 6
```

### Question 20 - *Medium*
**Question:** Show patient_id, first_name, last_name from patients whos diagnosis is 'Dementia'.

Primary diagnosis is stored in the admissions table.

```sql
select patient_id, first_name, last_name
from patients
join admissions
using (patient_id)
where diagnosis like "Dementia"
```

### Question 21 - *Medium*
**Question:** Display every patient's first_name.
Order the list by the length of each name and then by alphabetically.

```sql
with cte1 as (
select first_name, len(first_name)
from patients
order by 2 asc, 1 
)
select first_name
from cte1
```

### Question 22 - *Medium*
**Question:** Show the total amount of male patients and the total amount of female patients in the patients table.
Display the two results in the same row.

```sql
select
(select count(*)
from patients
where gender = "M")  as male,
(select count(*) 
from patients
where gender = "F") AS female
```

### Question 23 - *Medium*
**Question:** Show first and last name, allergies from patients which have allergies to either 'Penicillin' or 'Morphine'. Show results ordered ascending by allergies then by first_name then by last_name.

```sql
select first_name, last_name, allergies
from patients
where allergies IN ("Penicillin","Morphine")
order by allergies asc, first_name asc, last_name asc
```

### Question 24 - *Medium*
**Question:** Show patient_id, diagnosis from admissions. Find patients admitted multiple times for the same diagnosis.

```sql
select patient_id, diagnosis
from admissions
group by patient_id, diagnosis
having count(diagnosis) > 1
```

### Question 25 - *Medium*
**Question:** Show the city and the total number of patients in the city.
Order from most to least patients and then by city name ascending.

```sql
select city, count(*) as num_patients 
from patients
group by city
order by num_patients desc, city asc
```

### Question 26 - *Medium*
**Question:** Show first name, last name and role of every person that is either patient or doctor.
The roles are either "Patient" or "Doctor"

```sql
select first_name, last_name, 'Patient' as role 
from patients
union all
select first_name, last_name, 'Doctor' as role
from doctors
```

### Question 27 - *Medium*
**Question:** Show all allergies ordered by popularity. Remove NULL values from query.

```sql
select allergies, count() total_diagnosis
from patients
where allergies is not null
group by allergies
order by total_diagnosis desc
```

### Question 28 - *Medium*
**Question:** Show all patient's first_name, last_name, and birth_date who were born in the 1970s decade. Sort the list starting from the earliest birth_date.

```sql
select first_name, last_name, birth_date
from patients
where year(birth_date) between 1970 and 1979
order by birth_date asc
```

### Question 29 - *Medium*
**Question:** We want to display each patient's full name in a single column. Their last_name in all upper letters must appear first, then first_name in all lower case letters. Separate the last_name and first_name with a comma. Order the list by the first_name in decending order
EX: SMITH,jane

```sql
select concat(upper(last_name), ",",lower(first_name)) new_name_format
from patients
order by first_name desc
```

### Question 30 - *Medium*
**Question:** Show the province_id(s), sum of height; where the total sum of its patient's height is greater than or equal to 7,000.

```sql
select province_id, sum(height)
from patients
group by province_id
having sum(height) > 7000
order by 2 desc
```

### Question 31 - *Medium*
**Question:** Show the difference between the largest weight and smallest weight for patients with the last name 'Maroni'

```sql
select (
select max(weight) 
from patients
where last_name like "%maroni%") - (select min(weight) 
from patients
where last_name like "%maroni%") weight_delta
```

### Question 32 - *Medium*
**Question:** Show all of the days of the month (1-31) and how many admission_dates occurred on that day. Sort by the day with most admissions to least admissions.

```sql
select day(admission_date), count(*)
from admissions
group by day(admission_date)
order by 2 desc
```

### Question 33 - *Medium*
**Question:** Show all columns for patient_id 542's most recent admission_date.

```sql
select *
from admissions
where patient_id = 542
order by admission_date desc
LIMIT 1
```

### Question 34 - *Medium*
**Question:** Show patient_id, attending_doctor_id, and diagnosis for admissions that match one of the two criteria:
1. patient_id is an odd number and attending_doctor_id is either 1, 5, or 19.
2. attending_doctor_id contains a 2 and the length of patient_id is 3 characters.

```sql
select patient_id, attending_doctor_id, diagnosis
from admissions
where (patient_id %2 != 0 and attending_doctor_id in (1,5,19)) or (attending_doctor_id like "%2%" and len(patient_id) = 3)
```

### Question 35 - *Medium*
**Question:** Show first_name, last_name, and the total number of admissions attended for each doctor.

Every admission has been attended by a doctor.

```sql
select first_name, last_name, count(admission_date)
from admissions
join doctors
ON admissions.attending_doctor_id = doctors.doctor_id
group by first_name, last_name
```

### Question 36 - *Medium*
**Question:** For each doctor, display their id, full name, and the first and last admission date they attended.

```sql
select doctor_id, concat(first_name," ",last_name) as full_name, min(admission_date) as first_adminssion_date, max(admission_date) as last_adminssion_date
from admissions
join doctors
ON admissions.attending_doctor_id = doctors.doctor_id
group by doctor_id
```

### Question 37 - *Medium*
**Question:** Display the total amount of patients for each province. Order by descending.

```sql
select province_name, count(*) as patient_count
from patients
join province_names
using (province_id)
group by province_name
order by 2 desc
```

### Question 38 - *Medium*
**Question:** For every admission, display the patient's full name, their admission diagnosis, and their doctor's full name who diagnosed their problem.

```sql
select concat(p.first_name," ",p.last_name) patient_name, a.diagnosis, concat(d.first_name," ",d.last_name) doctor_name
from patients p
join admissions a
on p.patient_id = a.patient_id
join doctors d
on d.doctor_id = a.attending_doctor_id
```

### Question 39 - *Medium*
**Question:** display the first name, last name and number of duplicate patients based on their first name and last name.

Ex: A patient with an identical name can be considered a duplicate.

```sql
select first_name, last_name, count(first_name)
from patients
group by first_name, last_name
having count(first_name) >1
```

### Question 40 - *Medium*
**Question:** Display patient's full name,
height in the units feet rounded to 1 decimal,
weight in the unit pounds rounded to 0 decimals,
birth_date,
gender non abbreviated.

Convert CM to feet by dividing by 30.48.
Convert KG to pounds by multiplying by 2.205.

```sql
select
concat(first_name," ",last_name) full_name, round((height/30.48),1) Height_Feet, 
round((weight*2.205),0) weight_Pound, birth_date, 
case 
	when gender = "M" then "Male"
    else "Female"
end as gender_type
from patients
```

### Question 41 - *Medium*
**Question:** Show patient_id, first_name, last_name from patients whose does not have any records in the admissions table. (Their patient_id does not exist in any admissions.patient_id rows.)

```sql
select p.patient_id, first_name, last_name
from patients p
left join admissions a
on p.patient_id = a.patient_id
where a.patient_id is null
```

### Question 42 - *Medium*
**Question:** Display a single row with max_visits, min_visits, average_visits where the maximum, minimum and average number of admissions per day is calculated. Average is rounded to 2 decimal places.

```sql
select max(visit_count) max_visits, min(visit_count) min_visits, round(avg(visit_count),2) average_counts
from(
select admission_date, count(*) AS visit_count
from admissions
group by admission_date)
```

### Question 43 - *Hard*
**Question:** Show all of the patients grouped into weight groups.
Show the total amount of patients in each weight group.
Order the list by the weight group decending.

For example, if they weight 100 to 109 they are placed in the 100 weight group, 110-119 = 110 weight group, etc.

```sql
SELECT
  COUNT(*) AS patients_in_group,
  FLOOR(weight / 10) * 10 AS weight_group
FROM patients
GROUP BY weight_group
ORDER BY weight_group DESC;
```

### Question 44 - *Hard*
**Question:** Show patient_id, weight, height, isObese from the patients table.

Display isObese as a boolean 0 or 1.

Obese is defined as weight(kg)/(height(m)2) >= 30.

weight is in units kg.

height is in units cm.

```sql
SELECT
	patient_id, weight, height,
    case when weight/power(height*0.01,2) >= 30 then 1
    else 0
    end as isObese
FROM patients
```

### Question 45 - *Hard*
**Question:** Show patient_id, first_name, last_name, and attending doctor's specialty.
Show only the patients who has a diagnosis as 'Epilepsy' and the doctor's first name is 'Lisa'

Check patients, admissions, and doctors tables for required information.

```sql
select p.patient_id, p.first_name, p.last_name, d.specialty
from patients p
join admissions a
on p.patient_id = a.patient_id
join doctors d
on a.attending_doctor_id = d.doctor_id
where diagnosis = "Epilepsy" and d.first_name = "Lisa"
```

### Question 46 - *Hard*
**Question:** All patients who have gone through admissions, can see their medical documents on our site. Those patients are given a temporary password after their first admission. Show the patient_id and temp_password.

The password must be the following, in order:
1. patient_id
2. the numerical length of patient's last_name
3. year of patient's birth_date

```sql
select 
    patient_id, concat(patient_id, len(last_name), year(birth_date)) temp_password
from patients p
join admissions a
using (patient_id)
group by patient_id
```

### Question 47 - *Hard*
**Question:** Each admission costs $50 for patients without insurance, and $10 for patients with insurance. All patients with an even patient_id have insurance.

Give each patient a 'Yes' if they have insurance, and a 'No' if they don't have insurance. Add up the admission_total cost for each has_insurance group.

```sql
select
	case
    	when patient_id%2=0 then 'Yes'
    else 'No'
    end as has_insurance,
sum(case when patient_id%2 =0 then
    10
else
    50
end) as cost_after_insurance
from admissions
group by has_insurance
```

### Question 48 - *Hard*
**Question:** Show the provinces that has more patients identified as 'M' than 'F'. Must only show full province_name

```sql
SELECT pr.province_name
FROM patients AS pa
  JOIN province_names AS pr ON pa.province_id = pr.province_id
GROUP BY pr.province_name
HAVING
  COUNT( CASE WHEN gender = 'M' THEN 1 END) > COUNT( CASE WHEN gender = 'F' THEN 1 END);
```

### Question 49 - *Hard*
**Question:** We are looking for a specific patient. Pull all columns for the patient who matches the following criteria:
- First_name contains an 'r' after the first two letters.
- Identifies their gender as 'F'
- Born in February, May, or December
- Their weight would be between 60kg and 80kg
- Their patient_id is an odd number
- They are from the city 'Kingston'

```sql
select *
from patients
where first_name like "__R%" and gender = "F" and (MONTH(birth_date) in (2,5,12)) and weight between 60 and 80 and patient_id%2!=0 and city = "Kingston"
```

### Question 50 - *Hard*
**Question:** Show the percent of patients that have 'M' as their gender. Round the answer to the nearest hundreth number and in percent form.

```sql
SELECT 
   CONCAT(ROUND(SUM(gender='M') / CAST(COUNT(*) AS float), 4) * 100, '%') as percentage_of_M
FROM patients;
```

### Question 51 - *Hard*
**Question:** For each day display the total amount of admissions on that day. Display the amount changed from the previous date.

```sql
SELECT
 admission_date,
 count(admission_date) as admission_day,
 count(admission_date) - LAG(count(admission_date)) OVER(ORDER BY admission_date) AS admission_count_change 
FROM admissions
 group by admission_date
```

### Question 52 - *Hard*
**Question:** Sort the province names in ascending order in such a way that the province 'Ontario' is always on top.

```sql
with cte1 as (
select province_name,
	case
    	when province_name = "Ontario" then 1
    else 0
    end as ranks
from province_names
)
select province_name
from cte1
order by ranks desc
```

### Question 53 - *Hard*
**Question:** We need a breakdown for the total amount of admissions each doctor has started each year. Show the doctor_id, doctor_full_name, specialty, year, total_admissions for that year.

```sql
select doctors.doctor_id, concat(doctors.first_name," ",doctors.last_name) doctor_name, doctors.specialty, year(admissions.admission_date) as selected_year, count(admissions.admission_date) as total_admissions
from admissions
join doctors
on admissions.attending_doctor_id = doctors.doctor_id
group by doctors.doctor_id, doctor_name, doctors.specialty, selected_year
```
