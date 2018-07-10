---
title: 格式化自訂建置步驟或建置事件的輸出 | Microsoft Docs
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
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "33321346"
---
# <a name="formatting-the-output-of-a-custom-build-step-or-build-event"></a>格式化自訂建置步驟或建置事件的輸出
如果已正確格式化自訂建置步驟或建置事件的輸出，使用者會獲得下列好處：  
  
-   會在 [輸出] 視窗計算警告和錯誤。  
  
-   輸出會出現在 [工作清單] 視窗。  
  
-   按一下 [輸出] 視窗中的輸出會顯示適當的主題。  
  
-   [工作清單] 視窗或 [輸出] 視窗中已啟用 F1 作業。  
  
 輸出的格式應該是：  
  
 {*filename* (*line#* [, *column#*]) &#124; *toolname*} **:**  
  
 [*any text*] {**error** &#124; **warning**} *code####***:*** localizable string*  
  
 [ *any text* ]  
  
 其中：  
  
-   {*a* &#124; *b*} 是 *a* 或 *b* 的選擇。  
  
-   [`ccc`] 是選擇性的字串或參數。  
  
 例如:   
  
 C:\\*sourcefile.cpp*(134) : 錯誤 C2143: 語法錯誤 : 在 '}' 之前遺漏 ';'  
  
 LINK : 嚴重錯誤 LNK1104: 無法開啟檔案 '*'somelib.lib*'  
  
## <a name="see-also"></a>請參閱  
 [了解自訂建置步驟和建置事件](../ide/understanding-custom-build-steps-and-build-events.md)