---
title: 設定自訂建置步驟或建置事件的輸出格式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- builds [C++], build events
- custom build steps [C++], output format
- events [C++], build
- build events [C++], output format
- build steps [C++], output format
- builds [C++], custom build steps
ms.assetid: 92ad3e38-24d7-4b89-90e6-5a16f5f998da
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7da71e6391d2d3223b47ba528686d2fec003ab3a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="formatting-the-output-of-a-custom-build-step-or-build-event"></a>格式化自訂建置步驟或建置事件的輸出
如果已正確格式化自訂建置步驟或建置事件的輸出，使用者會獲得下列好處：  
  
-   警告和錯誤會算入**輸出**視窗。  
  
-   輸出會出現在**工作清單**視窗。  
  
-   按一下中的輸出**輸出**視窗會顯示適當的主題。  
  
-   F1 作業中啟用**工作清單**視窗或**輸出**視窗。  
  
 輸出的格式應該是：  
  
 {*filename* (*列 #* [，*資料行 #*]) &#124; *toolname*} **:**  
  
 [*任何文字*] {**錯誤** &#124; **警告**}*程式碼 # # #***:*** 可當地語系化的字串*  
  
 [*任何文字*]  
  
 其中：  
  
-   { &#124; *b*} 是任一個的選擇或*b*。  
  
-   [`ccc`] 是選擇性的字串或參數。  
  
 例如:   
  
 C:\\*sourcefile.cpp*(134): 錯誤 C2143： 語法錯誤： 遺漏 ';' 才能 '}'  
  
 連結： 嚴重錯誤 LNK1104： 無法開啟檔案 '*somelib.lib*'  
  
## <a name="see-also"></a>另請參閱  
 [了解自訂建置步驟和建置事件](../ide/understanding-custom-build-steps-and-build-events.md)