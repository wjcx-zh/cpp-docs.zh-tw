---
title: "逸出序列 | Microsoft Docs"
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
- "\r escape sequence"
- double backslash
- horizontal-tab 	 escape sequence
- (') single quotation mark
- "bell character \a escape sequence"
- escape sequences
- hexadecimal escape sequence
- carriage returns
- tab 	 escape sequence
- "\f escape sequence"
- quotation marks, single
- "formfeed \f escape sequence"
- "\v escape sequence"
- control character escape sequences
- " symbol in escape sequences"
- octal escape sequence
- escape characters
- "newline character \n escape sequence"
- nongraphic control characters
- question mark, literal
- "\nescape sequence"
- "vertical tab \v escape sequence"
- "\a escape sequence"
- '? symbol'
- '? symbol, escape sequence character'
- "	 escape sequence"
- backspace escape sequence
ms.assetid: 5aef377f-a76c-4d5c-aa04-8308758ad6a8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d341aa5af2b16d1a29bc4e3dfe2f97a68b73d6ba
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="escape-sequences"></a>逸出序列
由一個反斜線 (**\\**)，後面加上一個字母或數字組合所組成的字元組合，稱為「逸出序列」。 若要表示新行字元、單引號或字元常數中的某些其他字元，您必須使用逸出序列。 逸出序列視為單一字元，因此是有效的字元常數。  
  
 逸出序列通常用來指定終端機和印表機動作，例如歸位字元和定位鍵移動。 它們也可以用來提供非列印字元和通常具有特殊意義之字元 (例如雙引號 **"**) 的常值表示。 下表列出 ANSI 逸出序列，以及它們所表示的意義。  
  
 請注意，在問號前面加上反斜線 (**\\?**) 表示為常值問號，以避免字元序列被錯誤解譯為三併詞。 如需詳細資訊，請參閱[三併詞](../c-language/trigraphs.md)。  
  
### <a name="escape-sequences"></a>逸出序列  
  
|逸出序列|表示|  
|---------------------|----------------|  
|**\a**|鈴響 (警示)|  
|**\b**|退格鍵|  
|**\f**|Formfeed|  
|**\n**|換行|  
|**\r**|歸位字元|  
|**\t**|水平 Tab|  
|**\v**|垂直 Tab|  
|**\\'**|單引號|  
|**\\"**|雙引號|  
|**\\\\**|反斜線|  
|**\\?**|常值問號|  
|**\\** *ooo*|八進位標記法的 ASCII 字元|  
|**\x** *hh*|十六進位標記法的 ASCII 字元|  
|**\x** *hhhh*|十六進位標記法的 Unicode 字元，如果這個逸出序列用於寬字元常數或 Unicode 字串常值。<br /><br /> 例如，`WCHAR f = L'\x4e00'` 或 `WCHAR b[] = L"The Chinese character for one is \x4e00"`。|  
  
 **Microsoft 特定的**  
  
 如果反斜線後接著的字元未出現在上表中，編譯器會將這個未定義的字元視為字元本身。 例如，`\c` 會被視為 `c`。  
  
 **結束 Microsoft 特定的**  
  
 逸出序列可用來傳送非圖形控制字元至顯示裝置。 例如，在終端機或印表機上，ESC 字元 (**\033**) 通常用來做為控制命令的第一個字元。 有些逸出序列是裝置特定的。 例如，垂直 tab 字元和換頁字元逸出序列 (**\v** 和 **\f**) 不會影響螢幕輸出，但它們可執行適當的印表機操作。  
  
 您也可以使用反斜線 (**\\**) 做為接續字元。 當新行字元 (等同於按下 RETURN 鍵) 緊接在反斜線後面，編譯器會忽略反斜線和新行字元，並且將下一行視為上一行的一部分。 這主要用於大於單行的前置處理器定義。 例如:   
  
```  
#define assert(exp) \  
( (exp) ? (void) 0:_assert( #exp, __FILE__, __LINE__ ) )  
```  
  
## <a name="see-also"></a>請參閱  
 [C 字元常數](../c-language/c-character-constants.md)