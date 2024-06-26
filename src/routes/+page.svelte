<script lang="ts">
  interface Question {
    question: string;
    answer: string;
    value: 10 | 20 | 30;
    isQuotation: boolean;
  }
  const questions: Question[] = [
    {
      question: "What is the Bible?",
      answer:
        "The Bible is the inspired Word of God and is His revelation to all people of himself and His plan of salvation.",
      value: 10,
      isQuotation: false,
    },
    {
      question: "How many books are there in the Bible?",
      answer: "66",
      value: 10,
      isQuotation: false,
    },
    {
      question: "What are the two divisions of the Bible?",
      answer: "Old Testament and New Testament",
      value: 10,
      isQuotation: false,
    },
    {
      question: "How did God give us the Bible?",
      answer:
        "The Holy Spirit inspired holy men, giving them both the truth and the words to write.",
      value: 20,
      isQuotation: false,
    },
    {
      question: "What do we mean when we say the Bible is infallible?",
      answer: "The Bible cannot fail and has no errors.",
      value: 20,
      isQuotation: false,
    },
    {
      question: "What do we mean when we say the Bible is verbally inspired?",
      answer:
        "God inspired each word of the Bible, not just the thoughts or ideas.",
      value: 20,
      isQuotation: false,
    },
    {
      question:
        "What four natural or logical evidences do we have that the Bible is inspired?",
      answer:
        "Findings of archaeology; its unity; its endurance; its timelessness; its influence on people and nations; its many fulfilled prophecies",
      value: 30,
      isQuotation: false,
    },
    {
      question: "What five books of the Bible are called the 'Pentateuch'?",
      answer: "Genesis, Exodus, Leviticus, Numbers, Deuterotomy",
      value: 30,
      isQuotation: false,
    },
    {
      question: "What are the twelve books of Old Testament history?",
      answer:
        "Joshua, Judges, Ruth, 1 & 2 Samuel, 1 & 2 Kings, 1 & 2 Chronicles, Ezra, Nehemiah, Esther",
      value: 30,
      isQuotation: false,
    },
    {
      question: "What does 'testament' mean?",
      answer: "Covenant [contract or agreement]",
      value: 10,
      isQuotation: false,
    },
    {
      question: "Where did the universe come from?",
      isQuotation: true,
      value: 10,
      answer:
        "Genesis 1:1 In the beginning God created the heavens and the earth.",
    },
    {
      question: "Which is the first of the Ten Commandments?",
      isQuotation: true,
      value: 10,
      answer: "Exodus 20:3 You shall have no other gods before me.",
    },
    {
      question: "How long will the Bible last?",
      answer:
        "Matthew 24:35 Heaven and earth will pass away, but my words will never pass away.",
      value: 20,
      isQuotation: true,
    },
    {
      question: "Why is it important to memorize Bible verses?",
      answer:
        "Psalm 119:11 I have hidden your word in my heart that I might not sin against you.",
      value: 20,
      isQuotation: true,
    },
    {
      question:
        "According to Romans chapter eight, what things cannot separate us from God's love?",
      answer:
        "Romans 8:38,39 For I am convinced that neither death nor life, neither angels nor demons, neither the present nor the future, nor any powers, neither height nor depth, nor anything else in all creation, will be able to separate us from the love of God that is in Christ Jesus our Lord",
      value: 30,
      isQuotation: true,
    },
  ];

  let showAnswer = false;
  let currentQuestion = "";
  let currentAnswer = "";
  let quotationField = false;
  function handleTenPointQuestion() {
    showAnswer = false;
    const tenPointQuestions = questions.filter((q) => q.value === 10); // This line only selects the questions within the array that have a value of 10.
    const i = Math.floor(Math.random() * tenPointQuestions.length); // Depending on how many 10 point questions are within the array, the computer randomly chooses one of those questions the RNG way, with the numbers rounded down to the next integer
    currentQuestion = tenPointQuestions[i].question;
    currentAnswer = tenPointQuestions[i].answer;
    if (tenPointQuestions[i].isQuotation == true) {
      quotationField = true;
    } else {
      quotationField = false;
    }
  }
  function handleTwentyPointQuestion() {
    showAnswer = false;
    const twentyPointQuestions = questions.filter((q) => q.value === 20); // This line only selects the questions within the array that have a value of 10.
    const i = Math.floor(Math.random() * twentyPointQuestions.length); // Depending on how many 10 point questions are within the array, the computer randomly chooses one of those questions the RNG way, with the numbers rounded down to the next integer
    currentQuestion = twentyPointQuestions[i].question;
    currentAnswer = twentyPointQuestions[i].answer;
    if (twentyPointQuestions[i].isQuotation == true) {
      quotationField = true;
    } else {
      quotationField = false;
    }
  }
  function handleThirtyPointQuestion() {
    showAnswer = false;
    const thirtyPointQuestions = questions.filter((q) => q.value === 30); // This line only selects the questions within the array that have a value of 10.
    const i = Math.floor(Math.random() * thirtyPointQuestions.length); // Depending on how many 10 point questions are within the array, the computer randomly chooses one of those questions the RNG way, with the numbers rounded down to the next integer
    currentQuestion = thirtyPointQuestions[i].question;
    currentAnswer = thirtyPointQuestions[i].answer;
    if (thirtyPointQuestions[i].isQuotation == true) {
      quotationField = true;
    } else {
      quotationField = false;
    }
  }
  function revealAnswer() {
    showAnswer = true;
  }
</script>

<body>
  <h1>Welcome to JBQ Practice</h1>
  <p>
    Visit <a href="https://kit.svelte.dev">kit.svelte.dev</a> to read the documentation
  </p>
  <button class="tenpoint" on:click={handleTenPointQuestion}>
    10 Point Questions
  </button>
  <button class="twentypoint" on:click={handleTwentyPointQuestion}>
    20 Point Questions
  </button>
  <button class="thirtypoint" on:click={handleThirtyPointQuestion}>
    30 Point Questions
  </button><br /><br />
  <button class="really"> Real Match </button>
  <p>{currentQuestion}</p>
  {#if quotationField == true}
    <form>
      <label>Book</label>
      <input /><br />
      <label>Chapter</label>
      <input type="number" /><br />
      <label>Verse</label>
      <input type="number" /><br />
      <label>Quotation</label>
      <input type="text" class="quotationbox" />
    </form>
  {/if}
  <button on:click={revealAnswer}>Reveal Answer</button>
  {#if showAnswer == true}
    <p>{currentAnswer}</p>
  {/if}
</body>

<style>
  .tenpoint {
    color: greenyellow;
  }
  .twentypoint {
    color: yellow;
  }
  .thirtypoint {
    color: red;
  }
  .really {
    font-size: 40px;
  }
  .quotationbox {
    width: 50%;
    height: 50%;
  }
  body {
    background-color: black;
    color: white;
  }
</style>
