<script>
  let input = '';
  let output = '';
  const numbers = {
    "zero": 0,
    "one": 1,
    "two": 2,
    "three": 3,
    "four": 4,
    "five": 5,
    "six": 6,
    "seven": 7,
    "eight": 8,
    "nine": 9,
    "ten": 10,
    "eleven": 11,
    "twelve": 12,
    "thirteen": 13,
    "fourteen": 14,
    "fifteen": 15,
    "sixteen": 16,
    "seventeen": 17,
    "eighteen": 18,
    "nineteen": 19,
    "twenty": 20,
    // add more words as needed
  }

  function convertToDigits() {
    // convert input to lowercase
    let lowerInput = input.toLowerCase();
    // check if input is a number
    if (!isNaN(lowerInput)) {
        output = lowerInput;
    } else {
    // check if input is in numbers object
    output = numbers[lowerInput] || 'Invalid input';
    }
  }
</script>

<input type="text" bind:value={input}>
<button on:click={convertToDigits}>Convert</button>
<p>{output}</p>
