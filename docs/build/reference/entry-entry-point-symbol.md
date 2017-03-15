---
title: "/ENTRY (進入點符號) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/entry"
  - "VC.Project.VCLinkerTool.EntryPointSymbol"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/ENTRY 連結器選項"
  - "ENTRY 連結器選項"
  - "-ENTRY 連結器選項"
  - "開始位址"
ms.assetid: 26c62ba2-4f52-4882-a7bd-7046a0abf445
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# /ENTRY (進入點符號)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/ENTRY:function  
```  
  
## 備註  
 其中：  
  
 *Function \- 功用*  
 是一個指定 .exe 檔或 DLL 之使用者定義開始位址的函式。  
  
## 備註  
 \/ENTRY 選項會指定進入點函式做為 .exe 檔或 DLL 的開始位址。  
  
 這個函式必須以 `__stdcall` 呼叫慣例 \(Calling Convention\) 定義。  參數和傳回值取決於程式是主控台應用程式、Windows 應用程式或是 DLL。  建議您讓連結器設定進入點以便 C 執行階段程式庫能正確地初始化，而且靜態物件的 C\+\+ 建構函式也能夠被執行。  
  
 依預設值，開始位址是 C 執行階段程式庫中某一函式的名稱。  連結器會依據程式的屬性來選取它，如下表中所示。  
  
|函式名稱|預設為|  
|----------|---------|  
|**mainCRTStartup** \(或 **wmainCRTStartup**\)|使用 \/SUBSYSTEM:**CONSOLE** 的應用程式；呼叫 **main** \(或 **wmain**\)|  
|**WinMainCRTStartup** \(或 **wWinMainCRTStartup**\)|使用 \/SUBSYSTEM:**WINDOWS** 的應用程式；呼叫 `WinMain` \(或 **wWinMain**\)，它必須是以 `__stdcall` 定義的|  
|**\_DllMainCRTStartup**|DLL；呼叫 `DllMain`，它必須是以 `__stdcall` 定義的 \(如果存在的話\)|  
  
 如果沒有指定 [\/DLL](../../build/reference/dll-build-a-dll.md)或[\/SUBSYSTEM](../../build/reference/subsystem-specify-subsystem.md) 選項，連結器會依據是否已定義 **main** 或 `WinMain` 以選取一個子系統 \(Subsystem\) 和進入點。  
  
 函式 **main**、`WinMain` 和 `DllMain` 是三種不同形式的使用者定義進入點。  
  
 在建立 Managed 影像時，以 \/ENTRY 指定的功能必須擁有 \(LPVOID *var1*, DWORD *var2*, LPVOID *var3*\) 的簽章。  
  
 如需有關如何自行定義 DllMain 進入點的詳細資訊，請參閱[執行階段程式庫行為](../../build/run-time-library-behavior.md)。  
  
### 若要在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱[設定 Visual C\+\+ 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下 \[連結器\] 資料夾。  
  
3.  按一下 \[**進階**\] 屬性頁。  
  
4.  修改 \[進入點\] 屬性。  
  
### 若要以程式設計方式設定這個連結器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EntryPointSymbol%2A>。  
  
## 請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)