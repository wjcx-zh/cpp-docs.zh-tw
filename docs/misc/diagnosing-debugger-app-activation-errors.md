---
title: "診斷偵錯工具應用程式啟動錯誤 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.app_activation_failure"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 558ddc6d-0952-4617-84b8-0838717febcc
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "susanno"
manager: "douge"
---
# 診斷偵錯工具應用程式啟動錯誤
當您嘗試在 Visual Studio 偵錯工具中啟動 Windows 市集應用程式時，可能會收到下列其中一個錯誤：  
  
 **8061**  
  
```  
Unable to activate Windows Store app 'AppName'. The ProcessName process started, but the activation request failed with error 'ErrorNumber'  
```  
  
 **8062**  
  
```  
Unable to activate Windows Store app 'AppName'. The activation request failed with error 'ErrorNumber'  
```  
  
## 若要診斷這些錯誤  
 目前尚未提供確實可修正這些錯誤的方法。  請利用下列技術診斷問題。  
  
### 使用 \[事件檢視器\]  
  
1.  開啟 \[事件檢視器\] \(在 Windows \[開始\] 功能表中，搜尋 \[事件檢視器\]。\)在 \[事件檢視器\] 的樹狀結構中，巡覽至 **Application and Services Log\\Microsoft\\Windows\\Apps** 資料夾。  
  
2.  篩選檢視，只顯示事件 ID：5900\-6000  
  
3.  檢查記錄檔並查看發生的情況。  
  
### 使用原生偵錯工具  
 設定以原生偵錯工具執行專案。  
  
 在 Visual Studio 中，於啟始專案之屬性頁的 \[**偵錯**\] \(在 C\+\+ 和 JavaScript 中為 \[**偵錯**\]\) 頁面上，將 \[**偵錯工具類型**\] 設定為 \[**僅限原生**\]。  
  
 查看 \[輸出\] 視窗中所擲回的例外狀況。  建議您將偵錯工具設定為在這些例外狀況擲回時停止。  
  
## 修正應用程式授權錯誤  
 您可能會看一個啟動錯誤：「此應用程式無法啟動，因為其授權有問題」。您可以嘗試下列解決方法：  
  
-   在 \[組建\] 功能表上，選擇 \[清除方案\]，在 \[檔案總管\] 中開啟方案資料夾，並刪除 **bin** 和 **obj** 資料夾。  然後選擇 \[組建\]、\[重建方案\]。  重建方案會重新建立必要的資料夾。  
  
-   在 \[開始\] 畫面上選取應用程式，然後選擇應用程式列上的 \[解除安裝\]。  清除並重建您的方案。  
  
-   從以管理權限執行的命令提示字元中，使用 Powershell 命令來移除並重新安裝您的開發人員授權。  清除並重建您的方案。  請參閱[在命令提示字元中取得開發人員授權](http://msdn.microsoft.com/library/windows/apps/Hh974578.aspx#getting_a_developer_license_at_a_command_prompt)。