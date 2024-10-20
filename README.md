# zphisher
import amino
import os
def Tass2(data):
    listusers=[]
    for userId ,status in zip(data.userId,data.status):
       if status!=9 and status !=10:
           listusers.append(userId)
    return listusers
def Tass(data):
    listusers=[]
    for userId ,status in zip(data.profile.userId,data.profile.status):
       if status!=9 and status !=10:
           listusers.append(userId)
    return listusers
os.system('clear')

print("\033[1;32myoutube :  \033[1;37mhisyo")

print("\033[1;32m------------------------------------")

print("\033[1;38minsta :  \033[1;37mraqqauii_00")
client=amino.Client()
ss=0
sz=25
nuum=0
tst=False
while tst==False:
	try:
		email=input("\033[1;32m\n Email : \033[1;0m")
		password=input("\033[1;32m Password : \033[1;0m")
		client.login(email=email,password=password)
		tst=True
	except:
			tst=False
			print("\n Verify ur account! \n")
			exx=input(" continue? \033[1;32my/n : ")
			if exx=='N' or exx=='n' or exx=='no':
					os._exit(1)
            
infoos=input("\033[1;33m community lnk : \033[0m")
infoo=client.get_from_code(infoos)
comId=infoo.path[1:infoo.path.index("/")]
sub_client=amino.SubClient(comId=comId,profile=client.profile)
s=input("\033[1;33mchoose : \n\033[1;92mon \033[1;33m- online m \n\033[1;92mne \033[1;33m- new m \n\033[1;92mchoose name \033[1;33m: \033[0m")

maxo=int(input("\n\033[1;33m how members : \033[0m"))
cpt=0
if s=="on":
    os.system("clear")
    msg=input("\033[1;32m Message : ")
    nemmm=0
    cpt=0
    while maxo>nemmm and len(sub_client.get_online_users(start=nemmm,size=25).profile.userId)!=0:
        lista=sub_client.get_online_users(start= nemmm,size= 25)
        
        for userId in Tass(lista):
            try:
                sub_client.comment(userId=userId,message=msg)
                cpt=cpt+1
                print(cpt , "\033[1;93m ) \033[1;92m- \033[1;93muser id\033[1;92m =\033[0m ",userId)
            except:
                ffffff=True
        nemmm=nemmm+25
        
elif s=='ne':
    os.system("clear")
    msg=input("\033[1;32m Message : ")
    nemmm=0
    cpt=0
    while maxo>nemmm and len(sub_client.get_all_users(start=nemmm,size=25).profile.userId)!=0:
        listn=sub_client.get_all_users(start=0,size=25)
        
        for userId in Tass(listn):
            try:
                sub_client.comment(userId=userId,message=msg)
                cpt=cpt+1
                print(cpt , "\033[1;33m ) \033[1;92m-\033[1;33m user id \033[1;92m= \033[0m",userId)
            except:
                ffffff=True
                
        nemmm=nemmm+25
    
print("\033[1;92mall finished !\033[0m")
    
os._exit(1)
