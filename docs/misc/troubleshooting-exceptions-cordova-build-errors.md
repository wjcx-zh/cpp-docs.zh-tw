---
title: "例外狀況疑難排解：Cordova 建置錯誤 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BLD102"
  - "BLD10205"
  - "BLD301"
  - "BLD401"
  - "BLDErr_Build_NodeMissing"
  - "BLDErr_BLD_Win8Required"
ms.assetid: 781c09e3-0704-4b30-9230-036cbdb2dff9
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
---
# 例外狀況疑難排解：Cordova 建置錯誤
本主題描述使用 Visual Studio Tools for Apache Cordova 時，可能會看到的一些較常見的錯誤訊息。  
  
-   [MSBUILD: Cordova 建置錯誤 BLD102: 沒有這種檔案或目錄 'config.xml'](#BLD102)  
  
-   [MSBUILD: Cordova 建置錯誤 BLD301: 尚未設定遠端 iOS 組建代理程式](#BLD301)  
  
-   [MSBUILD: Cordova 建置錯誤 BLD401: 找不到模組 &lt;模組名稱&gt;](#BLD401)  
  
-   [MSBUILD: Cordova 建置錯誤 BLD10205: 請安裝 Android 目標](#BLD10205)  
  
-   [無法判斷 Node.js 可執行檔的 BLDErr_Build_NodeMissing 路徑。](#BLDErr_Build_NodeMissing)  
  
-   [BLDErr_Build_Win8Required](#BLDErr_Build_Win8Required)  
  
 如果您需要更概括性的說明，以替 Cordova 應用程式中的錯誤疑難排解，請參閱[解決建置錯誤](https://taco.visualstudio.com/en-us/docs/resolving-build-errors/)。  
  
##  <a name="BLD102"></a> MSBUILD: Cordova 建置錯誤 BLD102: 沒有這種檔案或目錄 'config.xml'  
 如果您看到此錯誤，請確定您的專案在專案根目錄中包含 config.xml 檔案，並確定您的專案是在本機電腦上，而不是在網路共用上。  
  
 如需詳細資訊，請參閱這篇 [StackOverflow 文章](http://stackoverflow.com/questions/27134007/new-cordova-project-gives-the-error-bld00102-no-such-file-or-directory-confi)。  
  
##  <a name="BLD301"></a> MSBUILD: Cordova 建置錯誤 BLD301: 尚未設定遠端 iOS 組建代理程式  
 完整錯誤字串為：  
  
-   MSBUILD: Cordova 建置錯誤 BLD301: 尚未設定遠端 iOS 組建代理程式。 請在 \[工具\] \> \[選項\] \> \[Apache Cordova 工具\] \> \[遠端代理程式組態\] 中設定一個。 如需詳細資訊和替代方案，請參閱 http:\/\/go.microsoft.com\/fwlink\/?LinkID\=511904  
  
 如需安裝和設定遠端 iOS 組建代理程式的資訊，請參閱 [iOS Setup Guide](http://taco.visualstudio.com/en-us/docs/ios-guide/)。  
  
##  <a name="BLD401"></a> MSBUILD: Cordova 建置錯誤 BLD401: 找不到模組 \<模組名稱\>  
 完整錯誤字串為：  
  
-   MSBUILD: Cordova 建置錯誤 BLD401: 錯誤: BLD00401: 找不到模組 \<模組名稱\>。 請移至 \[工具\] \-\-\> \[選項\] \-\-\> \[Apache Cordova 工具\] \-\-\> \[Cordova 工具\] \-\-\> \[清除 Cordova 快取\]，然後重試建置。  
  
 您可能需要清除快取，再重新安裝 vs\-tac。 如需詳細資訊，請參閱 [Re\-install vs\-tac](http://taco.visualstudio.com/en-us/docs/configure-vs-tools-apache-cordova#vstac)。  
  
 清除快取之後，刪除專案中的平台資料夾。 接著再試一次建置。  
  
##  <a name="BLD10205"></a> MSBUILD: Cordova 建置錯誤 BLD10205: 請安裝 Android 目標  
 如果您看到此錯誤，請確定已使用 Android SDK Manager \(SDK Manager.exe\)，安裝選取之目標裝置所需的相依項目。  
  
 如需所需的 API 層級和其他 Android SDK 元件的詳細資訊，請參閱 [Install dependencies manually](http://taco.visualstudio.com/en-us/docs/configure-vs-tools-apache-cordova#ThirdParty)。  
  
 您也應該確認 Visual Studio 用來尋找 Android SDK 的位置。 若要這樣做，請參閱 [Override system environment variables](http://taco.visualstudio.com/en-us/docs/configure-vs-tools-apache-cordova#env-var)。  
  
 如需安裝適當元件以使用工具的詳細資訊，請參閱 [third\-party tools](http://taco.visualstudio.com/en-us/docs/install-vs-tools-apache-cordova#choose)。  
  
##  <a name="BLDErr_Build_NodeMissing"></a> 無法判斷 Node.js 可執行檔的 BLDErr\_Build\_NodeMissing 路徑。  
 如果 Node.js 已安裝到非預設位置，Visual Studio 可能會找不到。 請將 Node.js 重新安裝到預設位置。 如需詳細資訊，請參閱這篇 [StackOverflow 文章](http://stackoverflow.com/questions/32203992/vs2015-cordova-apps-blderr-build-nodemissing) 和 [safely updating Node.js](http://taco.visualstudio.com/en-us/docs/change-node-version/) 的這篇文章。  
  
##  <a name="BLDErr_Build_Win8Required"></a> BLDErr\_Build\_Win8Required  
 若要在使用 Visual Studio Tools for Apache Cordova 建立的應用程式中以 Windows 為目標，則需要 Windows 8.1。