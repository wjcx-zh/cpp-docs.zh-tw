---
title: C 位元欄位 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- bitfields
- bit fields
ms.assetid: 9faf74c4-7fd5-4b44-ad18-04485193d06e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: af47bbebdf3b3a71e2b63b07a1fa467801728061
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32385672"
---
# <a name="c-bit-fields"></a>C 位元欄位
除了結構或等位成員的宣告子之外，結構宣告子也可以指定為位元數目 (稱為「位元欄位」)。 其長度是依冒號從欄位名稱的宣告子所設定。 位元欄位會以整數類型解譯。  
  
## <a name="syntax"></a>語法  
 *struct-declarator*：  
 *declarator*  
  
 *type-specifier declarator* opt **:** *constant-expression*  
  
 *constant-expression* 會以位元指定欄位的寬度。 `declarator` 的 *type-specifier* 必須是 `unsigned int`、**signed int** 或 `int`，而且 *constant-expression* 必須是非負值的整數值。 若該值是零，宣告沒有 `declarator`。 不允許位元欄位陣列、位元欄位指標與傳回位元欄位的函式。 選擇性的 `declarator` 會為位元欄位命名。 位元欄位只能宣告為結構的一部分。 address-of 運算子 (**&**) 無法套用至位元欄位元件。  
  
 無法參考未具名位元欄位，而且其內容在執行階段無法預測。 它們可以當作「虛設」欄位使用，以用於對齊用途。 未具名的位元欄位寬度指定為 0 時，可保證 *struct-declaration-list* 中跟隨在其後的成員儲存區是以 `int` 界限開始。  
  
 位元欄位也必須夠長，以包含位元模式。 例如，這兩個陳述式不合法：  
  
```  
short a:17;        /* Illegal! */  
int long y:33;     /* Illegal! */  
```  
  
 此範例定義名為 `screen` 之結構的二維陣列。  
  
```  
struct   
{  
    unsigned short icon : 8;  
    unsigned short color : 4;  
    unsigned short underline : 1;  
    unsigned short blink : 1;  
} screen[25][80];  
```  
  
 陣列包含 2,000 個元素。 每個元素都是個別的結構，其中包含四個位元欄位成員：`icon`、`color`、`underline` 與 `blink`。 每個結構的大小都是兩位元組。  
  
 位元欄位具有與整數類型相同的語意。 此表示位元欄位在運算式的使用方式，就像使用相同基底類型的變化一樣，而不論位元欄位中有多少位元。  
  
 **Microsoft 特定的**  
  
 定義為 `int` 的位元欄位會被視為帶正負號。 Microsoft 的 ANSI C 標準延伸模組允許為位元欄位使用 `char` 與 **long** 類型 (「帶正負號」與 `unsigned`)。 具有基底類型 **long**、**short** 或 `char` (「帶正負號」或 `unsigned`) 的未具名位元欄位會強制對齊基底類型適用的界限。  
  
 位元欄位是在整數內依最小顯著性到最高有效位元的順序配置。 在下列程式碼中  
  
```  
struct mybitfields  
{  
    unsigned short a : 4;  
    unsigned short b : 5;  
    unsigned short c : 7;  
} test;  
  
int main( void );  
{  
    test.a = 2;  
    test.b = 31;  
    test.c = 0;  
}  
```  
  
 位元排列如下：  
  
```  
00000001 11110010  
cccccccb bbbbaaaa  
```  
  
 因為 8086 系列處理器會先儲存整數值的低位元組，再儲存高位元組，上面的整數 `0x01F2` 將儲存到實體記憶體作為 `0xF2`，後面接著 `0x01`。  
  
 **結束 Microsoft 特定的**  
  
## <a name="see-also"></a>請參閱  
 [結構宣告](../c-language/structure-declarations.md)