<script>
  
  let number = 0;
  let numberInWords = "zero";

  const digits = ["zero","one", "two", "three", "four", "five", "six", "seven", "eight", "nine"];
  const tens = ["","ten","twenty","thirty","forty","fifty","sixty","seventy","eighty","ninety"];
  const teens = ["ten","eleven","twelve","thirteen","fourteen","fifteen","sixteen","seventeen","eighteen","nineteen"];
  const bigs = ["","thousand","million","billion","trillion","quadrillion","quintillion","sextillion","septillion","octillion","nonillion","decillion"];

  function convertToWords() {
    if (number === 0) {
      numberInWords = "zero";
      return;
    }
    
    numberInWords = "";
    let num = number;
    let bigIndex = -1;
    while (num > 0) {
      bigIndex++;
      let bigNumber = num % 1000;
      num = Math.floor(num / 1000);
      if (bigNumber === 0) {
        continue;
      }

      let smallNumber = "";
      if (bigNumber >= 100) {
        smallNumber += digits[Math.floor(bigNumber/100)] + " hundred ";
        bigNumber %= 100;
      }

      if (bigNumber >= 20) {
        smallNumber += tens[Math.floor(bigNumber/10)] + " ";
        bigNumber %= 10;
      } else if (bigNumber >= 10) {
        smallNumber += teens[bigNumber % 10] + " ";
        bigNumber = 0;
      }

      if (bigNumber > 0) {
        smallNumber += digits[bigNumber] + " ";
      }

      numberInWords = smallNumber + bigs[bigIndex] + " " + numberInWords;
    }
  }
</script>

<input type="number" bind:value={number} on:input={convertToWords} />
<p>{numberInWords}</p>
