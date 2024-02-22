# Roman-numerals
resole the roman to number and revert

```
<?php

class RomanToNumber {

    protected $roman;

    public function __construct($roman)
    {
        $this->roman = $roman; // Initialize the Roman numeral input.
    }

    public function romanToInt()
    {
        // Sort the array in descending order.
        $romanNumeralMap = array(
            'M' => 1000,
            'CM' => 900,
            'D' => 500,
            'CD' => 400,
            'C' => 100,
            'XC' => 90,
            'L' => 50,
            'XL' => 40,
            'X' => 10,
            'IX' => 9,
            'V' => 5,
            'IV' => 4,
            'I' => 1
        );

        $number = 0;
        foreach ($romanNumeralMap as $symbol => $value) {
            // $symbol retrieves the keys from the array.

            // Find the first occurrence position in the Roman input.
            while (strpos($this->roman, $symbol) === 0) {
                $number += $value;

                // Extracts the substring starting from the position of the current symbol.
                $this->roman = substr($this->roman, strlen($symbol));
            }
        }

        return $number; // Return the converted integer value.
    }

    public function intToRoman()
    {
        // Sort the array in descending order.
        $romanChar = array(
            'M' => 1000,
            'CM' => 900,
            'D' => 500,
            'CD' => 400,
            'C' => 100,
            'XC' => 90,
            'L' => 50,
            'XL' => 40,
            'X' => 10,
            'IX' => 9,
            'V' => 5,
            'IV' => 4,
            'I' => 1
        );

        $result = '';
        foreach ($romanChar as $key => $value) {
            // Loop through each key-value pair in the array.
            while ($this->roman >= $value) {
                $result .= $key;

                // Subtract the value from the input Roman numeral.
                $this->roman -= $value; 
            }
        }

        return $result; // Return the converted Roman numeral.
    }
}


$testString = new RomanToNumber(strtoupper("XXVVVii"));
$result = $testString->romanToInt();

print($result);
print('<br>');

$testNumber = new RomanToNumber(35);
$result = $testNumber->intToRoman();

print($result);

```
