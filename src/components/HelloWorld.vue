<template>
  <div class="hello">
    <!-- <h1>{{ msg }}</h1> -->
<label>Enter Sentence Here</label>&nbsp;

<input v-model="sentence">&nbsp;
<button @click="clickFunction()">Submit</button>

<div>The Longest Palindrome Is: {{currentStr}}</div>

</div>

</template>

<script>
export default {
  name: 'HelloWorld',
  // props: ["msg"],
  data() {
    return {
      sentence: " ",
      sentenceArray: [ ],
      palinRay: [ ],
      currentStr: ' ',
    }
  },

  computed: {
    // isPalindrome() {
    //   const {sentence} = this;
    //   return sentence === sentence.split(" ").reverse().join(" ");
    // }
  },

  methods: {
    //clickFunction function triggers all three functions to run one after each other.
    clickFunction() {
      //turns the entered sentence into an array of strings.
      this.sentenceArray = this.sentence.split(" "); 
        
        this.foundPalins();
        this.longestPalin();
      
      
    },
     //looks to see if a word in the array is a palindrome or not.  Passes through each word in the array.                 
    isPalindrome(word){

      //create variable "n" to hold the length of each of the word in the array
      let n = word.length;
      //strings have to be all lower-case to properly determine if it is a palindrome or not.
      word = word.toLowerCase();
      //for loop runs through to check each string [i] in the array and then reverese the word (n)
      for(let i = 0; i < n; i++, n--){
        //checks the current word [i] and sees if it is not the same in the reverse.
        if (word[i] != word[n-1])
        return false;

          return true;

      }
    },
    //function used to create an array of all the arrays in the array of strings.
    foundPalins() {
      //loops through the length of the sentence arrary
      for(let i = 0; i < this.sentenceArray.length; i++) {
        //uses the the isPalindrome function to chech each string in the array is a palindrome
        if(this.isPalindrome(this.sentenceArray[i])) {
          //if it is the string is pushed to a new array (palinRay) that holds all the palindromes.
          this.palinRay.push(this.sentenceArray[i]);
        }
      }
    },
    //function that loops through the palinRay array to find the longest palindrome
    longestPalin() {
      //creates a new arrary (currentStr) that goes through each palindrome in the palinRay array.
       this.currentStr = this.palinRay[0];
       //loops through all the palindrmes in the  palinRay array
      for(let i = 0; i < this.palinRay.length; i++) {
        //compares the length of current string in the palinRay against the length of the string in currentStr
        if(this.palinRay[i].length > this.currentStr.length) {
          //returns the longest palindrome.
         this.currentStr = this.palinRay[i];
        }

      }


    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
