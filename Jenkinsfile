node(slaveLabel) {
    checkoutCode()
    prepareVars()
    discordSend description: "Jenkins Pipeline Build ${appName}", footer: "Start Build", link: "$BUILD_URL", result: currentBuild.currentResult, title: JOB_NAME, webhookURL: "https://discordapp.com/api/webhooks/974610020517949491/Cv4es1VJju9LLLfa2MSVa9rKdBhhRHzFzXr0SwXO0M3SNcX4pWxJQTHlnnaNiu6YHIlY"// Webhook url discord

    switch(envName) {
      case ["dev", "sit", "uat"]:
        runUnitTest()
        runOWASP()
        runSonarQube()
        buildAndPushDockerImage()
        deployApp()
        // runPerfTest()
        break
      case "tag":
        buildAndPushDockerImage()
        break
      case "prod":
        checkoutCode(checkout_tag: true)
        deployApp()
        break
    }
  }
