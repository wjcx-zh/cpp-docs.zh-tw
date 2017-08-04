---
title: "字串常值串連 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- concatenating strings
- strings [C++], concatenating
ms.assetid: 51486b1f-4b1e-4061-9add-1aa38c6cdb3c
caps.latest.revision: 8
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: de466bd1bf5f0c8f8c1918f276e375f3da3bb215
ms.contentlocale: zh-tw
ms.lasthandoff: 05/18/2017

---
# <a name="string-literal-concatenation"></a>字串常值串連
若要形成佔用一行以上的字串常值，您可以串連兩個字串。 若要這麼做，請輸入一個反斜線，然後按下 RETURN 鍵。 反斜線會使編譯器忽略後方的新行字元。 例如，字串常值  
  
```  
"Long strings can be bro\  
ken into two or more pieces."  
```  
  
 與下列字串相同  
  
```  
"Long strings can be broken into two or more pieces."  
```  
  
 您之前可能會使用反斜線加上新行字元的方式來輸入一行以上的字串，現在您可以在這些位置上使用字串串連來取代。  
  
 若要在字串常值中強制增加新行，請如下所示在字串中想要中斷該行的位置輸入新行逸出序列 (**\n**)：  
  
```  
"Enter a number between 1 and 100\nOr press Return"  
```  
  
 由於字串可能會從原始程式碼的任何一列開始，且可以在任何後續程式碼列的任意資料行上接續，因此您可以排列字串的位置以加強原始程式碼的可讀性。 在任一種情況下，其螢幕上的表示在輸出時不會受到影響。 例如：  
  
```  
printf_s ( "This is the first half of the string, "  
           "this is the second half ") ;  
```  
  
 只要將字串的每個部分以雙引號括住，就會將各部分串連並以單一字串輸出。 這種串連是根據[轉譯階段](../preprocessor/phases-of-translation.md)指定的事件順序，在編譯期間進行。  
  
```  
"This is the first half of the string, this is the second half"  
```  
  
 字串指標 (會初始化為兩個不同的字串常值，只以空白字元分隔) 會儲存為單一字串 (指標會在[指標宣告](../c-language/pointer-declarations.md)中討論)。 若進行正確地參考時，如下列範例中所示，其結果會與上述範例相同：  
  
```  
char *string = "This is the first half of the string, "  
               "this is the second half";  
  
printf_s( "%s" , string ) ;  
```  
  
 在轉譯階段 6 中，由任何相鄰字串常值或相鄰寬字串常值的序列所指定的多位元組字元序列，會串連成單一多位元組字元序列。 因此，請勿將程式設計為允許執行時修改字串常值。 ANSI C 標準將修改字串的結果指定為未定義。  
  
## <a name="see-also"></a>另請參閱  
 [C 字串常值](../c-language/c-string-literals.md)
