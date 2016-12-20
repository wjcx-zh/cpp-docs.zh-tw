---
title: "/errorReport (回報編譯器內部錯誤) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCCLCompilerTool.ErrorReporting"
  - "/errorreport"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/errorReport 編譯器選項 [C++]"
  - "-errorReport 編譯器選項 [C++]"
ms.assetid: 819828f8-b0a5-412c-9c57-bf822f17e667
caps.latest.revision: 21
caps.handback.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /errorReport (回報編譯器內部錯誤)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

讓您直接向 Microsoft 提供內部編譯器錯誤 \(ICE\) 資訊。  
  
## 語法  
  
```  
/errorReport:[ none | prompt | queue | send ]  
```  
  
## Arguments  
 **none**  
 將不會收集有關內部編譯器錯誤的報告，也不會將報告傳送給 Microsoft。  
  
 **prompt**  
 提示您在收到內部編譯器錯誤時傳送報告。  當應用程式在開發環境中編譯時，預設值會是 **prompt**。  
  
 **queue**  
 將錯誤報告排入佇列。  當您用系統管理員權限登入時，就會顯示視窗，讓您能夠報告從上次登入以來的任何失敗 \(您所收到要傳送失敗報告的提示將不會超過每三天一次\)。  當應用程式在命令提示字元中編譯時，預設值會是 **queue**。  
  
 **send**  
 自動傳送內部編譯器錯誤報告給 Microsoft。  若要啟用這個選項，您必須先同意 Microsoft 的資料收集原則。  初次在電腦上指定 **\/errorReport:send** 時，編譯器訊息會指引您瀏覽包含 Microsoft 資料收集原則的網站。  
  
 這個選項取決於登錄設定。  如需如何在登錄中設定適當的值的詳細資訊， [如何開啟 Visual Studio 2008 命令列工具的自動錯誤報告](http://go.microsoft.com/fwlink/?LinkID=184695) 請參閱 MSDN 網站上。  
  
## 備註  
 當編譯器無法處理原始程式檔時，就會產生內部編譯器錯誤 \(ICE\)。  發生 ICE 時，編譯器不會產生輸出檔，也不會產生任何有用的診斷，供您用來修正程式碼。  
  
 在較早版本中，當您取得 ICE 時，都被鼓勵連絡 Microsoft 產品支援服務以報告問題。  以 **\/errorReport**，您可以直接提供 ICE 資訊給 Microsoft。  您的錯誤報告可以協助改善將來的編譯器版本。  
  
 使用者是否能夠傳送報告，完全是依電腦和使用者的原則權限而定。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱[如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
2.  按一下 \[**C\/C\+\+**\] 資料夾。  
  
3.  按一下 \[**進階**\] 屬性頁。  
  
4.  修改 \[**錯誤報告**\] 屬性。  
  
### 若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ErrorReporting%2A>。  
  
## 請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)