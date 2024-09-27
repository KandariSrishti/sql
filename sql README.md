--STEP 1
SELECT *
FROM crime_scene_report
WHERE type = 'murder'
AND city = 'SQL City'
AND date = 20180115

<img width="448" alt="image" src="https://github.com/user-attachments/assets/0b90e57c-ae78-4cee-900e-dc56b2fe7d20">

--STEP 2
SELECT *
FROM person
WHERE address_street_name = 'Northwestern Dr'
ORDER BY address_number DESC
LIMIT 1

<img width="458" alt="image" src="https://github.com/user-attachments/assets/d43bf9bc-cd57-4856-8b10-7b83241bd64c">

--STEP 3
SELECT *
FROM person
WHERE address_street_name = 'Franklin Ave'
LIMIT 10

<img width="355" alt="image" src="https://github.com/user-attachments/assets/35797d84-66c3-4b77-b6c7-c9e45019b109">

--STEP 4
SELECT *
FROM person
WHERE address_street_name = 'Franklin Ave'
AND name LIKE '%Annabel%'
LIMIT 10

<img width="355" alt="image" src="https://github.com/user-attachments/assets/672c5b9f-9c10-4bfa-b152-63400599f2bd">

--STEP 5
SELECT *
FROM interview
WHERE person_id IN (14887,16371) 
LIMIT 10

<img width="353" alt="image" src="https://github.com/user-attachments/assets/a6d12e92-7cca-4998-bf65-498bdd280851">

--STEP 6
SELECT *
FROM drivers_license
WHERE plate_number LIKE '%H42W%'
LIMIT 10

<img width="350" alt="image" src="https://github.com/user-attachments/assets/cb663bba-cfeb-4116-a694-2c0397554138">

--STEP 7
SELECT p. *
FROM drivers_license as d1
INNER JOIN person as p on d1.id = p.license_id
WHERE plate_number LIKE '%H42W%'
LIMIT 10

<img width="353" alt="image" src="https://github.com/user-attachments/assets/a913e27e-9715-44fa-8a12-0902b14f2bcf">

--STEP 8
SELECT p. *
FROM drivers_license as d1
INNER JOIN person as p on d1.id = p.license_id
INNER JOIN get_fit_now_member as gf on p.id = gf.person_id
WHERE plate_number LIKE '%H42W%'
LIMIT 10

<img width="359" alt="image" src="https://github.com/user-attachments/assets/d415ef8a-e9be-4778-9ddf-aba227079ee8">

--STEP 9
SELECT p. * , gf.*
FROM drivers_license as d1
INNER JOIN person as p on d1.id = p.license_id
LEFT JOIN get_fit_now_member as gf on p.id = gf.person_id
WHERE plate_number LIKE '%H42W%'
LIMIT 10

<img width="341" alt="image" src="https://github.com/user-attachments/assets/7fb51866-3abc-499e-9590-14f18bde018f">

--STEP 10
SELECT p. * , ci.*
FROM drivers_license as d1
INNER JOIN person as p on d1.id = p.license_id
INNER JOIN get_fit_now_member as gf on p.id = gf.person_id
INNER JOIN get_fit_now_check_in as ci on gf.id = ci.membership_id
WHERE plate_number LIKE '%H42W%'
AND membership_status = 'gold'
LIMIT 10

<img width="356" alt="image" src="https://github.com/user-attachments/assets/cf2778e3-44ad-4ec4-ab5e-4e24eaf386c7">

--STEP 11
SELECT p. * , ci.*
FROM drivers_license as d1
INNER JOIN person as p on d1.id = p.license_id
INNER JOIN get_fit_now_member as gf on p.id = gf.person_id
INNER JOIN get_fit_now_check_in as ci on gf.id = ci.membership_id
WHERE plate_number LIKE '%H42W%'
AND membership_status = 'gold'
AND check_in_date = 20180109
LIMIT 10

<img width="350" alt="image" src="https://github.com/user-attachments/assets/627879f8-5a3b-495d-8d2b-27fabbb55e49">

--STEP 12
<img width="360" alt="image" src="https://github.com/user-attachments/assets/b48a04cc-2c2a-4f44-a587-463d38171081">

--STEP 13
SELECT p.*, fb.*
FROM drivers_license as dl
INNER JOIN person as p on dl.id = p.license_id
INNER JOIN facebook_event_checkin as fb on fb.person_id = p.id
WHERE hair_color = 'red'
AND height >= 65
AND height <= 67
AND car_make = 'Tesla'
And car_model = 'Model S'
AND gender = 'female'
LIMIT 100

<img width="350" alt="image" src="https://github.com/user-attachments/assets/3a13b5f2-79be-419e-8b5e-438792155fcb">

--STEP 14
<img width="354" alt="image" src="https://github.com/user-attachments/assets/eda40da2-f3b5-4fc8-b758-78f352adf657">
