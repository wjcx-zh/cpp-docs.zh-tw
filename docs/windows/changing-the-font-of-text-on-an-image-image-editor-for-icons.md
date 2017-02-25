---
title: "Changing the Font of Text on an Image (Image Editor for Icons) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "fonts, changing on an image"
ms.assetid: b8849d40-d401-4e06-808f-e615cb2bee3b
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# Changing the Font of Text on an Image (Image Editor for Icons)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下列程序是進行以下作業的範例：  
  
-   將文字加入 Windows 應用程式中的圖示  
  
-   處理文字的字型  
  
### 若要變更影像上的文字字型  
  
1.  建立 C\+\+ Windows Form 應用程式。  如需詳細資訊，請參閱[建立 Windows 應用程式專案](http://msdn.microsoft.com/zh-tw/b2f93fed-c635-4705-8d0e-cf079a264efa)。  根據預設，[Windows Form 應用程式範本](http://msdn.microsoft.com/zh-tw/1babdebf-ab3f-4a64-a608-98499a5b9cea)會將名為 app.ico 的檔案加入專案中。  
  
2.  在 \[方案總管\] 中，按兩下檔案 app.ico，  就會開啟[影像編輯器](../mfc/image-editor-for-icons.md)。  
  
3.  從 \[影像\] 功能表中，選取 \[工具\]，然後選取 \[文字工具\]。  便會顯示[文字工具對話方塊](../mfc/text-tool-dialog-box-image-editor-for-icons.md)。  
  
4.  在 \[文字工具\] 對話方塊的空白文字區域中，輸入 `C++`。  這個文字將會顯示在影像編輯器之 app.ico 左上角的可調整方塊中。  
  
5.  在影像編輯器中，將可調整方塊拖曳至 app.ico 中心，以便改善文字的可讀性。  
  
6.  在 \[文字工具\] 對話方塊中，按一下 \[字型\] 按鈕。  便會顯示[文字工具字型對話方塊](../mfc/text-tool-font-dialog-box-image-editor-for-icons.md)。  
  
7.  在 \[文字工具字型\] 對話方塊中，從 \[字型\] 清單方塊所列的可用字型清單中，選取 \[Times New Roman\]。  
  
8.  從 \[字型樣式\] 清單方塊所列的可用字型樣式清單中，選取 \[粗體\]。  
  
9. 從 \[大小\] 清單方塊所列的可用點數大小清單中，選取 \[10\]。  
  
10. 按一下 \[確定\] 按鈕。  \[文字工具字型\] 對話方塊將會關閉，而且新的字型設定便會套用至文字。  
  
11. 按一下 \[文字工具\] 對話方塊上的 \[關閉\] 按鈕。  文字周圍的可調整方塊便會從影像編輯器中消失。  
  
## 請參閱  
 [Editing Graphical Resources](../mfc/editing-graphical-resources-image-editor-for-icons.md)   
 [Toolbar](../mfc/toolbar-image-editor-for-icons.md)