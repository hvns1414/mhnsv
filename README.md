import paramiko
def wizard():
    rabbit = """
        / \__
       (    @\___
       /         O
      /   (_____/
     /_____/   U
    """
    print(rabbit)
    
    print("""
    [1]ssh command      
    [2]help
    [3]exit   
        
        """)
    
wizard()

a=input(">>> ")

if a=="1":
    ip=input("host: ")
    com=input("command: ")
    usr=input("usr: ")
    passwd=input("passwd: ")
    def execute_ssh_command(host, user, password, command):
        ssh = paramiko.SSHClient()
        ssh.set_missing_host_key_policy(paramiko.AutoAddPolicy())
        ssh.connect(host, username=user, password=password)
        stdin, stdout, stderr = ssh.exec_command(command)
        output = stdout.read().decode()
        ssh.close()
        return output

    host = ip
    user = usr
    password = passwd
    command = com

    output = execute_ssh_command(host, user, password, command)
    print(output)
    print("[+]ssh")
elif a=="2":
    print("host ip usr user passwd pasword command echo werd")
else:
    exit()
