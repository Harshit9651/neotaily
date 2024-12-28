<template>
  <div class="code-editor-page">
    <div class="question-section">
      <h2 class="header">Programming Challenge</h2>
      <div class="question-card">
        <p class="question">{{ question }}</p>
      </div>
    </div>

    <div class="editor-output-section">
      <div class="editor-container">
        <h3 class="section-title">Code Editor</h3>
        <div id="monaco-editor"></div>
      </div>
      <div class="output-container">
        <h3 class="section-title">Output</h3>
        <div class="output-display">{{ output }}</div>
      </div>
    </div>
  </div>
</template>

<script>
import * as monaco from "monaco-editor";

export default {
  data() {
    return {
      question: "",
      editor: null,
      output: "Your output will be displayed here...",
    };
  },
  mounted() {
    // Fetch question from backend
    this.fetchQuestion();

    // Initialize Monaco Editor
    this.editor = monaco.editor.create(document.getElementById("monaco-editor"), {
      value: "// Write your code here...\n",
      language: "javascript",
      theme: "vs-dark",
      automaticLayout: true,
    });

    // Add editor change listener
    this.editor.onDidChangeModelContent(() => {
      this.handleCodeChange();
    });
  },
  methods: {
    fetchQuestion() {
      // Replace with your backend endpoint
      fetch("https://your-backend-api.com/get-question")
        .then((response) => response.json())
        .then((data) => {
          this.question = data.question || "Default question";
        })
        .catch((error) => {
          console.error("Error fetching question:", error);
        });
    },
    handleCodeChange() {
      const code = this.editor.getValue();
      try {
        // Execute the code (for demonstration purposes, using eval - use with caution)
        const result = eval(code);
        this.output = result.toString();
      } catch (error) {
        this.output = `Error: ${error.message}`;
      }
    },
  },
};
</script>

<style lang="scss" scoped>
.code-editor-page {
  background: #000;
  color: #fff;
  font-family: 'Roboto', sans-serif;
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 20px;
  min-height: 100vh;

  .question-section {
    width: 100%;
    max-width: 800px;
    margin-bottom: 20px;

    .header {
      color: #2cbb5d;
      font-size: 24px;
      margin-bottom: 10px;
    }

    .question-card {
      background: #121212;
      border: 1px solid #2cbb5d;
      border-radius: 8px;
      padding: 15px;
      box-shadow: 0 4px 10px rgba(44, 187, 93, 0.3);
      font-size: 18px;
      line-height: 1.5;
    }
  }

  .editor-output-section {
    display: flex;
    justify-content: space-between;
    width: 100%;
    max-width: 1200px;

    .editor-container,
    .output-container {
      flex: 1;
      margin: 0 10px;

      .section-title {
        color: #2cbb5d;
        font-size: 20px;
        margin-bottom: 10px;
      }

      #monaco-editor {
        height: 400px;
        border: 1px solid #2cbb5d;
        border-radius: 8px;
        box-shadow: 0 4px 10px rgba(44, 187, 93, 0.3);
      }

      .output-display {
        height: 400px;
        background: #121212;
        border: 1px solid #2cbb5d;
        border-radius: 8px;
        padding: 10px;
        overflow-y: auto;
        box-shadow: 0 4px 10px rgba(44, 187, 93, 0.3);
        white-space: pre-wrap;
      }
    }
  }

  @media (max-width: 768px) {
    flex-direction: column;

    .editor-output-section {
      flex-direction: column;

      .editor-container,
      .output-container {
        margin: 10px 0;
      }
    }
  }
}
</style>
