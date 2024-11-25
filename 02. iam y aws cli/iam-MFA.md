# IAM - Forma de proteger las cuentas

## Password Policy

- Contraseñas fuertes: mayor seguridad para tu cuenta.
- En aws puede asignar una politica de contarseña.
    - Tamaño minimo de contarseña
    - Requerir caracteres especificos
        - mayusculas, minusculas
        - numeros
        - caracteres no alfanumericos
    - Permitir a todos los usuarios IAM cambair su contarseña
    - Expiración de contraseña
    - impedir reuso de contraseña.

## Multi Factor Authentication = MFA

- Usar el MFA en la cuenta root y cuentas IAM
- MFA = Contraseña que tu sabes + security device you own (un dispositivo de seguridad de cual eres dueño)
- beneficio principal
    - si la contraseña es robada o hackeada la cuenta no se compremente.

### MFA DEVICE options in AWS

1. **Virtual MFA device**

- Google authenticator (phone)
- Authy (phone)

2. **Universal 2nd Factor (U2F) Security Key**

- YubiKey by Yubico (soporta multiple root y usuarios IAM)





