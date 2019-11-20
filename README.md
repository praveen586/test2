# test2
CModifyRequest modifyRequest = new CModifyRequest();

modifyRequest.returnData = "everything";

//--
CPSOID psoID = new CPSOID
{
ID = "CN=group1,OU=IT,DC=dc1,DC=win,DC=company,DC=com"
};

modifyRequest.psoID = psoID;


List<modification> modif = new List<modification>();

modif.Add(CreateModification("member", "add", new object[] { "CN=user1,OU=IT,DC=dc1,DC=win,DC=company,DC=com" }));


modifyRequest.modification = modif.ToArray();

//-- Create web service instance
ActiveRolesSPMLProviderSoapClient webService = new ActiveRolesSPMLProviderSoapClient();

webService.ClientCredentials.UserName.UserName = @"userName";
webService.ClientCredentials.UserName.Password = @"password";


//-- Send request and get response
CModifyResponse myresponse = webService.modify(modifyRequest);

///---- CreateMo

dification function

modification CreateModification(string name, string operation, object[] values)
{
modification modif = new modification
{
operation = operation,
name = name,
value = values
};

return modif;
}

   

