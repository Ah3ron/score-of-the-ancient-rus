<script>
  let inputNumber = 0;
  let outputText = "Ноль";

  let wholeNumbers = [
    "целковый",
    "пара",
    "четверик",
    "осьмерик",
    "пудовик",
    "медяк",
    "серебряк",
    "золотник",
    "осьмик",
    "девятик",
    "десятик",
  ];

  let fractionalNumbers = [
    "полушка",
    "четвертушка",
    "осьмушка",
    "пудовичок",
    "медячок",
    "серебрячок",
    "золотничок",
    "осьмичок",
    "девятичок",
    "десятичок",
  ];

  function convert() {
    if (inputNumber >= 2048) {
      outputText =
        "Русы не ведают чисел больше чем десятик, да девятик, да осьмик, да золотник, да серебряк, да медяк, да пудовик, да осьмерик, да четверик, да пара, да целковый, да полушка, да четвертушка, да осьмушка, да пудовичок, да медячок, да серебрячок, да золотничок, да осьмичок, да девятичок, да десятичок";
      return;
    } else if (inputNumber === 0) {
      outputText = "Ноль";
      return;
    } else if (inputNumber < 0) {
      outputText =
        "Отрицательные числа придумали евреи чтобы обманывать русов.";
      return;
    }

    let binaryString = inputNumber.toString(2);

    if (binaryString.indexOf(".") !== -1) {
      binaryString = binaryString.slice(0, binaryString.indexOf(".") + 11);
    }

    let integerPart = binaryString.split(".")[0];
    let fractionalPart = binaryString.split(".")[1];

    let outputArray = [];
    for (let i = 0; i < integerPart.length; i++) {
      if (integerPart[i] === "0") {
        continue;
      }
      outputArray.push(wholeNumbers[integerPart.length - i - 1]);
    }

    if (fractionalPart) {
      for (let i = 0; i < fractionalPart.length; i++) {
        if (fractionalPart[i] === "0") {
          continue;
        }
        outputArray.push(fractionalNumbers[i]);
      }
    }

    outputArray[0] = outputArray[0][0].toUpperCase() + outputArray[0].slice(1);
    outputText = outputArray.join(", да ");
  }
</script>

<div class="container h-full mx-auto flex justify-center md:items-center">
  <div class="space-y-10 flex flex-col items-center">
    <h2 class="h2">Перевод в счет древних русов.</h2>
    <div class="flex flex-col md:flex-row items-center gap-4">
      <input
        class="w-full md:min-w-[380px] input p-3"
        bind:value={inputNumber}
        on:input={convert}
        type="number"
        name="input"
        id=""
      />
      <div class="w-full md:min-w-[380px] card p-3">
        {outputText}
      </div>
    </div>
  </div>
</div>
