
E-HealthCare-Management-System(ehms)

```
uri-root-path
ehms-service/api/v1
```

##### 查詢醫生
```
GET
/doctor 條列所有醫生
/doctor?id= 根據doctor_id 來查詢醫生
```

Response
```
{
	"doctor_id":
	"doctor_first_name":
	"doctor_last_name":
	"doctor_gender":
	"doctor_contact_number":
	"doctor_age":
	"doctor_entry_charge":
	"doctor_qualification":
	"doctor_type":
	"doctor_email":
}
```

新增醫生
```
POST
/doctor
```

Request
```
{
	"doctor_first_name":
	"doctor_last_name":
	"doctor_gender":
	"doctor_contact_number":
	"doctor_age":
	"doctor_entry_charge":
	"doctor_qualification":
	"doctor_type":
	"doctor_email":
}
```

Response
200


##### 刪除醫生
```
Delete
/doctor？id=
```
Response
200
400

##### 新增病人
```
POST
/patient
```

Request 
```JSON
{
	"patient_first_name":
	"patient_last_name":
	"patient_gender":
	"patient_cn":
	"patient_age":
	"patient_email_address":
	"patient_blood_group":
	"patient_address":
}
```

Response
200

##### 查詢病人 
```
GET
/patient?id=
```

Response
```JSON
{
	"patient_id":
    "patient_first_name":
	"patient_last_name":
	"patient_gender":
	"patient_cn":
	"patient_age":
	"patient_email_address":
	"patient_blood_group":
	"patient_address":
}
```
##### 查看回饋
```
GET
/feedback
/feedback?location= 查詢特定部門的回饋
```

##### Response
```JSON
[
	 {
	 "feedback_patient_id":
	 "feedback_point":
	 "feedback_doctor_nature":
	 "feedback_location":
	 "feedback_patient_comment":
	 }
]
```

##### 查看醫囑

```
GET
/report？patient_id= 特定病人的所有醫囑
/report?patient_id= & doctor_id= 特定病人看特定醫生的醫囑
/report?doctor_id= 特定醫生下達的所有醫囑
```

##### Repsone
```JSON
{
	"report_id": "",
	"report_appointment_id": "",
	"report_patient_id": "",
 	"report_doctor_id": "",
 	"report_prescribed_medicine": "",
 	"report_doctor_comment": ""
}
```

##### 查詢預約
```
GET
/appointment 查詢所有預約
/appointment/{doctor_id}
/appointment/{patient_id}
```

##### Response
```JSON
[
	{
		"appointment_id" : "",
		"appointment_problem": "",
		"appointment_patient_id": "",
		"appointment_docker_id": "",
		"appointment_doctor_type": "",
		"appointment_qualification": "",
		"appointment_doctor_fee": "",
		"appointment_payment_status": "",
		"appointment_status": ""
	}
]
```

original functions
[[Role]]