```ts
class CheckingAccount {
    public function open(float $initialAmount) {
        // Código para abrir la cuenta y guardarlo en la base de datos
    }
}

class BusinessCheckingAccount extends CheckingAccount {
    public function open(float $initialAmount) {
        if ($initialAmount < 1000) {
            throw new Exception("Las cuentas empresariales deben tener un depósito inicial de 1.000 euros");
        }
        parent::open($initialAmount);
    }
}

class PersonalCheckingAccount extends CheckingAccount {
    public function open(float $initialAmount) {
        if ($initialAmount <= 0) {
            throw new Exception("Las cuentas personales deben tener un depósito inicial superior a cero euros");
        }
        parent::open($initialAmount);
    }
}

```