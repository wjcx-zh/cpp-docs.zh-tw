---
title: "char、 wchar_t、 char16_t、 char32_t |Microsoft 文件"
ms.custom: 
ms.date: 02/14/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- char_cpp
- char16_t_cpp
- wchar_t_cpp
- char32_t_cpp
dev_langs:
- C++
ms.assetid: 6b33e9f5-455b-4e49-8f12-a150cbfe2e5b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a87eff9801b2754909159ef4d5e2c24c079ee8f1
ms.sourcegitcommit: 23a0ddd271bbcc31631283542981ff5f1693d27f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/15/2018
---
# <a name="char-wchart-char16t-char32t"></a>char、wchar_t、char16_t、char32_t
型別**char**， **wchar_t**， **char16_t**和**char32_t**代表英數字元的內建類型，以及非英數字符和非列印字元。

## <a name="syntax"></a>語法

```cpp  
char     ch1{ 'a' };  // or { u8'a' }   
wchar_t  ch2{ L'a' };    
char16_t ch3{ u'a' };    
char32_t ch4{ U'a' };  
```  
  
## <a name="remarks"></a>備註

**Char**類型是在 C 和 c + + 中的原始字元類型。 型別**unsigned char**通常用來表示*位元組*，這不是 c + + 中的內建型別。 **Char**類型可以用來儲存來自 ASCII 字元集、 任何 iso-8859 字元集和個別的位元組的多位元組字元，例如 Shift JIS 或 Unicode 字元集的 utf-8 編碼的字元。 字串的**char**類型稱為*縮小*字串，即使使用多位元組字元編碼。 Microsoft 編譯器， **char**是 8 位元類型。

**Wchar_t**類型是實作所定義的寬字元類型。 在 Microsoft 編譯器，它代表的是 16 位元寬字元，用來儲存 Unicode 編碼為 UTF-8 16LE，在 Windows 作業系統上的原生字元類型。 寬字元版本的通用 C 執行階段 (UCRT) 程式庫函式使用**wchar_t**和其指標和陣列類型做為參數和傳回值，執行原生 Windows API 的寬字元版本。

**Char16_t**和**char32_t**類型分別代表 16 位元和 32 位元寬字元。 Unicode 編碼為 utf-16 可以儲存在**char16_t**類型和編碼為 utf-32 可以儲存在 Unicode **char32_t**型別。 這些類型的字串和**wchar_t**是所有稱為*寬*字串，但通常指的字串皆是特別為了**wchar_t**型別。

C + + 標準程式庫，`basic_string`針對窄和寬字串特製化類型。 使用`std::string`字元屬於類型**char**，`std::u16string`字元屬於類型**char16_t**，`std::u32string`字元屬於類型**char32_t**，和`std::wstring`字元屬於類型**wchar_t**。 其他代表文字的類型包括`std::stringstream`和`std::cout`具有窄和寬字串的特製化。  
  
