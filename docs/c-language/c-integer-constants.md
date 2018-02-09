---
title: "C 整數常數 | Microsoft Docs"
ms.custom: 
ms.date: 02/01/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- integer constants
ms.assetid: fcf6b83c-2038-49ec-91ca-3d5ca1f83037
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6c23e90d235e1ad2a8cca577c5cfbf2be55b52b6
ms.sourcegitcommit: 30ab99c775d99371ed22d1a46598e542012ed8c6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2018
---
# <a name="c-integer-constants"></a>C 整數常數

「整數常數」為代表整數值的十進位 (基底 10)、八進位 (基底 8) 或十六進位 (基底 16) 數字。 使用整數常數來表示無法變更的整數值。

## <a name="syntax"></a>語法

*integer-constant*：  
&nbsp;&nbsp;*decimal-constant* *integer-suffix*<sub>opt</sub>  
&nbsp;&nbsp;*octal-constant* *integer-suffix*<sub>opt</sub>  
&nbsp;&nbsp;*hexadecimal-constant* *integer-suffix*<sub>opt</sub>  

*decimal-constant*：  
&nbsp;&nbsp;*nonzero-digit*  
&nbsp;&nbsp;*decimal-constant* *digit*  

*octal-constant*：  
&nbsp;&nbsp;**0**  
&nbsp;&nbsp;*octal-constant* *octal-digit*  

*hexadecimal-constant*：  
&nbsp;&nbsp;**0x**  *hexadecimal-digit*  
&nbsp;&nbsp;**0X**  *hexadecimal-digit*  
&nbsp;&nbsp;*hexadecimal-constant* *hexadecimal-digit*  

*nonzero-digit*：下列其中一個  
&nbsp;&nbsp;**1 2 3 4 5 6 7 8 9**  

*octal-digit*：下列其中一個  
&nbsp;&nbsp;**0 1 2 3 4 5 6 7**  

*hexadecimal-digit*：下列其中一個  
&nbsp;&nbsp;**0 1 2 3 4 5 6 7 8 9**  
&nbsp;&nbsp;**a b c d e f**  
&nbsp;&nbsp;**A B C D E F**  
  
*integer-suffix*：  
&nbsp;&nbsp;*unsigned-suffix* *long-suffix*<sub>opt</sub>  
&nbsp;&nbsp;*long-suffix* *unsigned-suffix*<sub>opt</sub>  
&nbsp;&nbsp;*unsigned-suffix* *64-bit-integer-suffix*<sub>opt</sub>

*unsigned-suffix*：下列其中一個  
&nbsp;&nbsp;**u U**  

*long-suffix*：下列其中一個  
&nbsp;&nbsp;**l L**  
  
*64-bit-integer-suffix*：&nbsp;&nbsp;**i64 I64** 之一  

除非前面加上負號 (**-**)，否則整數常數為正數。 負號會解譯為一元算術負運算子  (如需這個運算子的詳細資訊，請參閱[一元算術運算子](../c-language/unary-arithmetic-operators.md))。

如果整數常數的開頭是 **0x** 或 **0X** 開始，即為十六進位。 如果開頭是數字 **0**，即為八進位。 否則即假設為十進位。

下列各行是相等的：

```C
0x1C   /* = Hexadecimal representation for decimal 28 */
034    /* = Octal representation for decimal 28 */
```

空白字元不能分隔整數常數的數字。 下列範例示範有效的十進位、八進位和十六進位常數。

```C
/* Decimal Constants */
10
132
32179

/* Octal Constants */
012
0204
076663

/* Hexadecimal Constants */
0xa or 0xA
0x84
0x7dB3 or 0X7DB3
```

## <a name="see-also"></a>另請參閱

[C 常數](../c-language/c-constants.md)  
