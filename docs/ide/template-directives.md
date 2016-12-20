---
title: "範本指示詞 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "[!else] 範本指示詞"
  - "[!endif] 範本指示詞"
  - "[!endloop] 範本指示詞"
  - "[!if] 範本指示詞"
  - "[!loop] 範本指示詞"
  - "[!output] 範本指示詞"
  - "自訂精靈, 範本指示詞"
  - "指示詞, 範本指示詞"
  - "else 指示詞 ([!else])"
  - "endif 指示詞 ([!endif])"
  - "endloop 指示詞 ([!endloop])"
  - "if 指示詞 ([!if])"
  - "loop 指示詞 ([!loop])"
  - "output 指示詞 ([!output])"
  - "範本指示詞"
ms.assetid: b6204153-813a-423c-b044-e39c352cc5af
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 範本指示詞
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可在精靈的[樣板檔案](../ide/template-files.md)和 [Templates.inf 檔案](../ide/templates-inf-file.md)中使用下列樣板指示詞來自訂精靈。  
  
|指示詞|描述|  
|---------|--------|  
|\[\!  if \]|開始一個控制結構，來檢查某條件。|  
|\[\!  else \]|\[\!  if \] 控制結構的定義。  檢查另一個條件。|  
|\[\!  endif \]|結束 \[\!  if \] 控制結構的定義。|  
|\[\!  output \]|其用法有下列兩種：<br /><br /> -   \[\!  output "string" \] 提供字串。<br />-   \[\!  output SYMBOL\_STRING \] 提供符號 SYMBOL\_STRING 的值。|  
|\[\!  loop \]|其用法有下列兩種：<br /><br /> -   \[\!  loop \= 5 \]<br />-   \[\!  loop \= *NUM\_OF\_PAGES* \]，其中 *NUM\_OF\_PAGES* 是一個含數值的符號。|  
|\[\!  endloop \]|結束迴圈 \(Loop\) 結構。|  
  
 左括號 \(\[\) 後緊接著驚嘆號 \(\!\) 表示樣板指示詞的開頭。  右括號則表示樣板指示詞的結尾。  這是必要的語法：  
  
```  
[!directive params]  
```  
  
 在 *directive* 和  *params* 之間必須有空格或非識別項字元。  
  
## 範例  
  
```  
[!if SAMPLE_RADIO_OPTION1]  
You have checked the option 'Sample radio button option 1'  
[!else]  
You have checked the option 'Sample radio button option 2'  
[!endif]  
```  
  
 您可在樣板檔案中搭配使用下列的運算子與上述指示詞。  
  
```  
+  
-     
=  
!=     
==     
||     
&&    
!  
```  
  
## 範例  
  
```  
[!if SYMBOL_STRING != 0]  
```  
  
## 請參閱  
 [您的精靈所建立的檔案](../ide/files-created-for-your-wizard.md)   
 [自訂精靈](../ide/custom-wizard.md)   
 [建立自訂精靈](../ide/creating-a-custom-wizard.md)   
 [設計精靈](../ide/designing-a-wizard.md)