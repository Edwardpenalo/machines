
<img width="1035" height="307" alt="image" src="https://github.com/user-attachments/assets/1c0fbf93-6e4e-4909-85bd-fcf3be683a96" />

<img width="738" height="132" alt="image" src="https://github.com/user-attachments/assets/34c73c30-8f43-40b4-9dc3-e4af8a4487ee" />

<img width="1222" height="667" alt="image" src="https://github.com/user-attachments/assets/026cdd4e-c254-4b63-a366-b43da1666f51" />

<img width="1281" height="274" alt="image" src="https://github.com/user-attachments/assets/339867ce-6379-46e9-8117-ff1798979426" />

<img width="977" height="875" alt="image" src="https://github.com/user-attachments/assets/acb5aec7-72c0-4369-ba23-4d553627db5e" />

function verifyInviteCode(code)
	{
	var formData=
		{
		"code":code
	};
	$.ajax(
		{
		type:"POST",dataType:"json",data:formData,url:'/api/v1/invite/verify',success:function(response)
			{
			console.log(response)
		}
		,error:function(response)
			{
			console.log(response)
		}
	}
	)
}
function makeInviteCode()
	{
	$.ajax(
		{
		type:"POST",dataType:"json",url:'/api/v1/invite/how/to/generate',success:function(response)
			{
			console.log(response)
		}
		,error:function(response)
			{
			console.log(response)
		}
	}
	)
}
