---
title: "格式化自訂建置步驟或建置事件的輸出 | Microsoft Docs"
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
  - "建置事件 [C++], 輸出格式"
  - "建置步驟 [C++], 輸出格式"
  - "組建 [C++], 建置事件"
  - "組建 [C++], 自訂建置步驟"
  - "自訂建置步驟 [C++], 輸出格式"
  - "事件 [C++], 組建"
ms.assetid: 92ad3e38-24d7-4b89-90e6-5a16f5f998da
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 格式化自訂建置步驟或建置事件的輸出
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果有正確格式化自訂建置步驟或建置事件的輸出，使用者就能獲得下列好處：  
  
-   \[**輸出**\] 視窗中會計算警告與錯誤的次數。  
  
-   輸出會顯示在 \[**工作清單**\] 視窗中。  
  
-   按一下 \[**輸出**\] 視窗中的輸出會顯示適當的主題。  
  
-   \[**工作清單**\] 視窗或 \[**輸出**\] 視窗中的 F1 作業已啟用。  
  
 輸出的格式應如下：  
  
 {*filename* \(*line\#* \[, *column\#*\]\) &#124; *toolname*} **:**  
  
 \[*any text*\] {**error** &#124; **warning**} *code\#\#\#\#***:** *localizable string*  
  
 \[ *any text* \]  
  
 其中：  
  
-   {*a* &#124; *b*} 意指對 *a* 或 *b* 的選擇。  
  
-   \[`ccc`\] 為選擇性字串或參數。  
  
 例如：  
  
 C:\\*sourcefile.cpp*\(134\) : 錯誤 C2143：語法錯誤: '}' 之前遺漏 ';'  
  
 連結：嚴重錯誤 LNK1104：無法開啟檔案 '*somelib.lib*'  
  
## 請參閱  
 [了解自訂建置步驟和建置事件](../ide/understanding-custom-build-steps-and-build-events.md)