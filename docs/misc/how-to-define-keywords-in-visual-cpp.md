---
title: "如何：定義 Visual C++ 關鍵字 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "使用者關鍵字"
  - "保留字, 使用者定義的關鍵字"
  - "使用者定義的關鍵字"
  - "保留的關鍵字, 使用者定義"
  - "usertype.dat"
  - "關鍵字 [C++], 使用者定義"
ms.assetid: 2dfcf343-e861-4bde-b5a4-7deb6773d9c8
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 如何：定義 Visual C++ 關鍵字
關鍵字是具有特殊意義的預先定義保留識別項。 您不能在程式中將關鍵字當做識別項使用。 不過，您可以定義自己的關鍵字以用於 Visual C\+\+，也可以為關鍵字指派自訂的語法著色。 語法著色可為您提供有關程式碼結構和狀態的視覺提示。  
  
### 定義您自己的 Visual C\+\+ 關鍵字  
  
1.  使用 Visual Studio [程式碼和文字編輯器](http://msdn.microsoft.com/zh-tw/508e1f18-99d5-48ad-b5ad-d011b21c6ab1)或 Notepad.exe，來建立名為 `usertype.dat` 的純文字檔案。  
  
2.  在 `usertype.dat` 中，分行輸入每個使用者定義的關鍵字。  
  
3.  將 `usertype.dat` 儲存在包含 devenv.exe 的目錄中。 根據預設，該目錄的路徑是 *\<磁碟機\>*:\\Program Files\\[!INCLUDE[TLA#tla_visualstu](../misc/includes/tlasharptla_visualstu_md.md)]*\<主要版本號碼.次要版本號碼\>*\\Common7\\[!INCLUDE[TLA2#tla_ide](../build/includes/tla2sharptla_ide_md.md)]。 由於該目錄預設為唯讀，因此您需要系統管理認證才能儲存 `usertype.dat`。  
  
4.  結束 Visual Studio，然後重新啟動。  
  
    > [!NOTE]
    >  您無法在編輯工作階段期間將 `usertype.dat` 檔案重新命名或重新載入，因為在初始化期間會讀取該檔案。 所有之前定義的色彩設定會優先考慮，因為語法著色機制最後才會檢查 `usertype.dat` 檔案。  
  
5.  在 \[**工具**\] 功能表上按一下 \[**選項**\]。 在 \[選項\] 對話方塊中，按一下 \[環境\]，然後按一下 \[字型和色彩\]，然後按一下 \[顯示項目:\] 清單中的 \[C\/C\+\+ 使用者關鍵字\]。  
  
6.  設定使用者定義之關鍵字的字型和色彩屬性，如[選項對話方塊、環境、字型和色彩](../Topic/Fonts%20and%20Colors,%20Environment,%20Options%20Dialog%20Box.md)中所述。  
  
 如需詳細資訊，請參閱[C\+\+ 關鍵字](../cpp/keywords-cpp.md)。  
  
## 請參閱  
 [以使用者群組的成員身分執行](../top/running-as-a-member-of-the-users-group.md)   
 [預設鍵盤快速鍵](../Topic/Default%20Keyboard%20Shortcuts%20in%20Visual%20Studio.md)