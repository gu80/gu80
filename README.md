from cryptography. fernet import Fernet


def generate_key():
    key = Fernet.generate_key()
    with open("key.key", "wb") as key_file: 
        key_file.write(key)
        
        
def load_key():
    return open("key.key", "rb").read()


def encrypt_file(file_path):
    key = load_key()
    fernet = Fernet(key)
    
    with open(file_path, "rb") as file:
        original = file.read()
        
    encrypted = fernet.encrypt(original)
    
    with open(file_path, "wb") as file:
        file.write(encrypted)
        
generate_key()
encrypt_file("aqui e o local do seu hack exemplo c:\hack")
