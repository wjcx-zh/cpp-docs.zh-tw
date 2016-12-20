---
title: "/STUB (MS-DOS Stub 檔名) | Microsoft Docs"
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
  - "/stub"
  - "VC.Project.VCLinkerTool.DosStub"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/STUB 連結器選項"
  - "MS-DOS Stub 檔案名稱連結器選項"
  - "STUB 連結器選項"
  - "-STUB 連結器選項"
  - "Win32 [C++], 附加 MS-DOS Stub 程式"
  - "Windows API [C++], 附加 MS-DOS Stub 程式"
ms.assetid: 65221ffe-4f9a-4a14-ac69-3cfb79b40b5f
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /STUB (MS-DOS Stub 檔名)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/STUB:filename  
```  
  
## 備註  
 其中：  
  
 *filename*  
 是一個 MS\-DOS 應用程式。  
  
## 備註  
 \/STUB 選項會將 MS\-DOS Stub 程式附加到 Win32 程式。  
  
 如果檔案是在 MS\-DOS 中執行，Stub 程式便會被叫用。  它通常會顯示適當的訊息；不過，任何有效的 MS\-DOS 應用程式都可以是 Stub 程式。  
  
 請在命令列上分號 \(:\) 後面指定 Stub 程式的 *filename*。  連結器會檢查 *filename*，如果這個檔案不是可執行檔便會發出錯誤訊息。  程式必須為 .exe 檔；.com 檔不是有效的 Stub 程式。  
  
 如果沒有使用這個選項，連結器會附加一個發出下列訊息的預設 Stub 程式：  
  
```  
This program cannot be run in MS-DOS mode.  
```  
  
 在建立虛擬裝置驅動程式時，*filename* 可以讓使用者指定一個含有 IMAGE\_DOS\_HEADER 結構 \(定義於 WINNT.H 中\) 的檔案名稱使用於 VXD 中，而非預設的標頭。  
  
### 若要在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱[設定 Visual C\+\+ 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下 \[連結器\] 資料夾。  
  
3.  按一下 \[**命令列**\] 屬性頁。  
  
4.  在 \[**其他選項**\] 方塊中輸入選項。  
  
### 若要以程式設計方式設定這個連結器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。  
  
## 請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)