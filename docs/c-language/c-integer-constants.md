---
title: "C 整數常數 | Microsoft Docs"
ms.custom: 
ms.date: 02/27/2018
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
ms.openlocfilehash: e0f28b41c54b14c9e673d3fb8e7bb4947206cfd3
ms.sourcegitcommit: d24de38f9da844f824acb9d200a3f263077145fc
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2018
---
# <a name="c-integer-constants"></a>C 整數常數

「整數常數」為代表整數值的十進位 (底數為 10)、八進位 (底數為 8) 或十六進位 (底數為 16) 數字。 使用整數常數來表示無法變更的整數值。

## <a name="syntax"></a>語法

*integer-constant*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*decimal-constant* *integer-suffix*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*octal-constant* *integer-suffix*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*hexadecimal-constant* *integer-suffix*<sub>opt</sub><br/>

*decimal-constant*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*nonzero-digit*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*decimal-constant* *digit*<br/>

*octal-constant*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*octal-constant* *octal-digit*<br/>

*hexadecimal-constant*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*hexadecimal-prefix* *hexadecimal-digit*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*hexadecimal-constant* *hexadecimal-digit*<br/>

*hexadecimal-prefix*：下列其中一個<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0x**  **0X**<br/>

*nonzero-digit*：下列其中一個<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**1 2 3 4 5 6 7 8 9**<br/>

*octal-digit*：下列其中一個<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0 1 2 3 4 5 6 7**<br/>

*hexadecimal-digit*：下列其中一個<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0 1 2 3 4 5 6 7 8 9**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**a b c d e f**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**A B C D E F**<br/>

*integer-suffix*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unsigned-suffix* *long-suffix*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unsigned-suffix* *long-long-suffix*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unsigned-suffix* *64-bit-integer-suffix*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*long-suffix* *unsigned-suffix*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*long-long-suffix* *unsigned-suffix*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*64-bit-integer-suffix*<br/>

*unsigned-suffix*：下列其中一個<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**u U**<br/>

*long-suffix*：下列其中一個<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**l L**<br/>

*long-long-suffix*：下列其中一個<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**ll LL**<br/>

*64-bit-integer-suffix*：下列其中一個<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**i64 I64**<br/>

**i64** 與 **I64** 均為 Microsoft 特定的尾碼。

除非前面加上負號 (**-**)，否則整數常數為正數。 負號會解譯為一元算術負運算子  (如需這個運算子的詳細資訊，請參閱[一元算術運算子](../c-language/unary-arithmetic-operators.md))。

如果整數常數的開頭是 **0x** 或 **0X** 開始，即為十六進位。 如果開頭是數字 **0**，即為八進位。 否則即假設為十進位。

下列是相等的整數常數：

```C
28
0x1C   /* = Hexadecimal representation for decimal 28 */
034    /* = Octal representation for decimal 28 */
```

空白字元不能分隔整數常數的數字。 下列範例示範部分有效的十進位、八進位和十六進位常數。

```C
    /* Decimal Constants */
    int                 dec_int    = 28;
    unsigned            dec_uint   = 4000000024u;
    long                dec_long   = 2000000022l;
    unsigned long       dec_ulong  = 4000000000ul;
    long long           dec_llong  = 9000000000LL;
    unsigned long long  dec_ullong = 900000000001ull;
    __int64             dec_i64    = 9000000000002I64;
    unsigned __int64    dec_ui64   = 90000000000004ui64;

    /* Octal Constants */
    int                 oct_int    = 024;
    unsigned            oct_uint   = 04000000024u;
    long                oct_long   = 02000000022l;
    unsigned long       oct_ulong  = 04000000000UL;
    long long           oct_llong  = 044000000000000ll;
    unsigned long long  oct_ullong = 044400000000000001Ull;
    __int64             oct_i64    = 04444000000000000002i64;
    unsigned __int64    oct_ui64   = 04444000000000000004uI64;

    /* Hexadecimal Constants */
    int                 hex_int    = 0x2a;
    unsigned            hex_uint   = 0XA0000024u;
    long                hex_long   = 0x20000022l;
    unsigned long       hex_ulong  = 0XA0000021uL;
    long long           hex_llong  = 0x8a000000000000ll;
    unsigned long long  hex_ullong = 0x8A40000000000010uLL;
    __int64             hex_i64    = 0x4a44000000000020I64;
    unsigned __int64    hex_ui64   = 0x8a44000000000040Ui64;
```

## <a name="see-also"></a>另請參閱

[C 常數](../c-language/c-constants.md)<br/>
