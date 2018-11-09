---
title: is、isw 常式
ms.date: 11/04/2016
apilocation:
- msvcr110_clr0400.dll
- msvcr90.dll
- msvcr80.dll
- msvcr100.dll
- msvcr110.dll
- msvcr120.dll
apitype: DLLExport
f1_keywords:
- isw
- is
helpviewer_keywords:
- is routines
- isw routines
ms.assetid: 1e171a57-2cde-41f6-a75f-a080fa3c12e5
ms.openlocfilehash: 65dc5bbfbaeab59e91cdca23c4f0f01b5ef7ebbb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50620166"
---
# <a name="is-isw-routines"></a>is、isw 常式

|||
|-|-|
|[isalnum、iswalnum、_isalnum_l、_iswalnum_l](../c-runtime-library/reference/isalnum-iswalnum-isalnum-l-iswalnum-l.md)|[isgraph、iswgraph、_isgraph_l、_iswgraph_l](../c-runtime-library/reference/isgraph-iswgraph-isgraph-l-iswgraph-l.md)|
|[isalpha、iswalpha、_isalpha_l、_iswalpha_l](../c-runtime-library/reference/isalpha-iswalpha-isalpha-l-iswalpha-l.md)|[isleadbyte、_isleadbyte_l](../c-runtime-library/reference/isleadbyte-isleadbyte-l.md)|
|[isascii、__isascii、iswascii](../c-runtime-library/reference/isascii-isascii-iswascii.md)|[islower、iswlower、_islower_l、_iswlower_l](../c-runtime-library/reference/islower-iswlower-islower-l-iswlower-l.md)|
|[isblank、iswblank、_isblank_l、_iswblank_l](../c-runtime-library/reference/isblank-iswblank-isblank-l-iswblank-l.md)|[isprint、iswprint、_isprint_l、_iswprint_l](../c-runtime-library/reference/isprint-iswprint-isprint-l-iswprint-l.md)|
|[iscntrl、iswcntrl、_iscntrl_l、_iswcntrl_l](../c-runtime-library/reference/iscntrl-iswcntrl-iscntrl-l-iswcntrl-l.md)|[ispunct、iswpunct、_ispunct_l、_iswpunct_l](../c-runtime-library/reference/ispunct-iswpunct-ispunct-l-iswpunct-l.md)|
|[iscsym、iscsymf、__iscsym、\__iswcsym、\__iscsymf、\__iswcsymf、_iscsym_l、_iswcsym_l、_iscsymf_l、_iswcsymf_l](../c-runtime-library/reference/iscsym-functions.md)|[isspace、iswspace、_isspace_l、_iswspace_l](../c-runtime-library/reference/isspace-iswspace-isspace-l-iswspace-l.md)|
|[_isctype、iswctype、_isctype_l、_iswctype_l](../c-runtime-library/reference/isctype-iswctype-isctype-l-iswctype-l.md)|[isupper、_isupper_l、iswupper、_iswupper_l](../c-runtime-library/reference/isupper-isupper-l-iswupper-iswupper-l.md)|
|[isdigit、iswdigit、_isdigit_l、_iswdigit_l](../c-runtime-library/reference/isdigit-iswdigit-isdigit-l-iswdigit-l.md)|[isxdigit、iswxdigit、_isxdigit_l、_iswxdigit_l](../c-runtime-library/reference/isxdigit-iswxdigit-isxdigit-l-iswxdigit-l.md)|

## <a name="remarks"></a>備註

這些常式會測試所指定條件的字元。

針對任何從 -1 (`EOF`) 到 **UCHAR_MAX** (0xFF) (含) 的整數引數，**is** 函式會產生有意義的結果。 預期的引數類型是 `int`。

> [!CAUTION]
> 針對 **is** 常式，傳遞類型 `char` 的引數可能會產生無法預期的結果。 值大於 0x7F 之 `char` 類型的 SBCS 或 MBCS 單一位元組字元是負數。 如果傳遞 `char`，編譯器可能會將值轉換為帶正負號 `int` 或帶正負號 **long**。 此值可能是由編譯器進行 sign-extended，並產生非預期的結果。

針對任何從 -1 (**WEOF**) 到 0xFFFF 的整數引數，**isw** 函式會產生有意義的結果。 在 WCHAR.H 中，將 **wint_t** 資料類型定義為 **unsigned short**；它可以保留任何寬字元或寬字元檔案結尾 (**WEOF**) 值。

輸出值會受到地區設定的 `LC_CTYPE` 分類設定影響；如需詳細資訊，請參閱 [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)。 這些沒有 **_l** 尾碼的函式版本，會針對此與地區設定相關的行為使用目前的地區設定；具有 **_l** 尾碼的版本也一樣，只不過它們會改用傳遞的地區設定參數。

在 "C" 地區設定中，**is** 常式的測試條件如下：

`isalnum`<br/>
英數字元 (A-Z、a-z 或 0-9)。

`isalpha`<br/>
字母 (A-Z 或 a-z)。

`__isascii`<br/>
ASCII 字元 (0x00 - 0x7F)。

`isblank`<br/>
水平定位或空白字元 (0x09 或 0x20)。

`iscntrl`<br/>
控制字元 (0x00 - 0x1F 或 0x7F)。

`__iscsym`<br/>
字母、底線或數字。

`__iscsymf`<br/>
字母或底線。

`isdigit`<br/>
十進位數字 (0 - 9)。

`isgraph`<br/>
不含空格 ( ) 的可列印字元。

`islower`<br/>
小寫字母 (a - z)。

`isprint`<br/>
含空格的可列印字元 (0x20 - 0x7E)。

`ispunct`<br/>
標點符號字元。

`isspace`<br/>
空白字元 (0x09 - 0x0D 或 0x20)。

`isupper`<br/>
大寫字母 (A - Z)。

`isxdigit`<br/>
十六進位數字 (A-F、a-f 或 0-9)。

針對 **isw** 常式，所指定條件的測試結果與地區設定無關。 **isw** 函式的測試條件如下：

`iswalnum`<br/>
`iswalpha` 或 `iswdigit`。

`iswalpha`<br/>
任何屬於其中一個實作定義之字元集的寬字元，且 `iswcntrl`、`iswdigit`、`iswpunct` 或 `iswspace` 都不是非零值。 `iswalpha` 只會針對寬字元傳回非零值，且 `iswupper` 或 `iswlower` 是非零值。

`iswascii`<br/>
ASCII 字元的寬字元表示 (0x0000 - 0x007F)。

`iswblank`<br/>
對應至標準空白字元或屬於其中一個實作定義之寬字元集的寬字元，且 `iswalnum` 為 false。 標準空白字元是空白 (L' ') 和水平定位字元 (L'\t')。

`iswcntrl`<br/>
控制寬字元。

`__iswcsym`<br/>
`isalnum` 為 true 的任何寬字元，或 '_' 字元。

`__iswcsymf`<br/>
`iswalpha` 為 true 的任何寬字元，或 '_' 字元。

`iswctype`<br/>
字元具有 `desc` 引數所指定的屬性。 針對 `iswctype` 之 `desc` 引數的每個有效值，都有對等的寬字元分類常式，如下表所示︰

### <a name="equivalence-of-iswctypec-desc-to-other-isw-testing-routines"></a>iswctype(c, desc) 與其他 isw 測試常式的對應項

|*desc* 引數的值|iswctype( *c, desc*) 對應項|
|------------------------------|----------------------------------------|
|**_ALPHA**|**iswalpha(** `c` **)**|
|**_ALPHA** &#124; **_DIGIT**|**iswalnum(** `c` **)**|
|**_BLANK**|**iswblank(** `c` **)**|
|**_CONTROL**|**iswcntrl(** `c` **)**|
|**_DIGIT**|**iswdigit(** `c` **)**|
|**_ALPHA** &#124; **_DIGIT** &#124; **_PUNCT**|**iswgraph(** `c` **)**|
|**_LOWER**|**iswlower(** `c` **)**|
|**_ALPHA** &#124; **_BLANK** &#124; **_DIGIT** &#124; **_PUNCT**|**iswprint(** `c` **)**|
|**_PUNCT**|**iswpunct(** `c` **)**|
|**_BLANK**|**iswblank(** `c` **)**|
|**_SPACE**|**iswspace(** `c` **)**|
|**_UPPER**|**iswupper(** `c` **)**|
|**_HEX**|**iswxdigit(** `c` **)**|

`iswdigit`<br/>
對應至十進位數字字元的寬字元。

`iswgraph`<br/>
不含空白寬字元 (L' ') 的可列印寬字元。

`iswlower`<br/>
小寫字母，或其中一個實作定義的寬字元集，且 `iswcntrl`、`iswdigit`、`iswpunct` 或 `iswspace` 都不是非零值。 只有針對對應至小寫字母的寬字元，`iswlower` 才會傳回非零值。

`iswprint`<br/>
含空白寬字元 (L' ') 的可列印寬字元。

`iswpunct`<br/>
既非空白寬字元 (L' ') 且 `iswalnum` 非為非零值之寬字元的可列印寬字元。

`iswspace`<br/>
對應至標準空白字元或屬於其中一個實作定義之寬字元集的寬字元，且 `iswalnum` 為 false。 標準空白字元如下：空白 (L' ')、換頁字元 (L'\f')、新行字元 (L'\n')、歸位字元 (L'\r')、水平定位字元 (L'\t') 和垂直定位字元 (L'\v')。

`iswupper`<br/>
大寫或屬於其中一個實作定義之寬字元集的寬字元，且 `iswcntrl`、`iswdigit`、`iswpunct` 或 `iswspace` 都不是非零值。 只有針對對應至大寫字元的寬字元，`iswupper` 才會傳回非零值。

`iswxdigit`<br/>
對應至十六進位數字字元的寬字元。

## <a name="example"></a>範例

```C
// crt_isfam.c
/* This program tests all characters between 0x0
* and 0x7F, then displays each character with abbreviations
* for the character-type codes that apply.
*/

#include <stdio.h>
#include <ctype.h>

int main( void )
{
   int ch;
   for( ch = 0; ch <= 0x7F; ch++ )
   {
      printf( "%.2x  ", ch );
      printf( " %c", isprint( ch )  ? ch   : ' ' );
      printf( "%4s", isalnum( ch )  ? "AN" : "" );
      printf( "%3s", isalpha( ch )  ? "A"  : "" );
      printf( "%3s", __isascii( ch )  ? "AS" : "" );
      printf( "%3s", iscntrl( ch )  ? "C"  : "" );
      printf( "%3s", __iscsym( ch )  ? "CS "  : "" );
      printf( "%3s", __iscsymf( ch )  ? "CSF"  : "" );
      printf( "%3s", isdigit( ch )  ? "D"  : "" );
      printf( "%3s", isgraph( ch )  ? "G"  : "" );
      printf( "%3s", islower( ch )  ? "L"  : "" );
      printf( "%3s", ispunct( ch )  ? "PU" : "" );
      printf( "%3s", isspace( ch )  ? "S"  : "" );
      printf( "%3s", isprint( ch )  ? "PR" : "" );
      printf( "%3s", isupper( ch )  ? "U"  : "" );
      printf( "%3s", isxdigit( ch ) ? "X"  : "" );
      printf( ".\n" );
   }
}
```

## <a name="output"></a>輸出

```Output
00            AS  C                              .
01            AS  C                              .
02            AS  C                              .
03            AS  C                              .
04            AS  C                              .
05            AS  C                              .
06            AS  C                              .
07            AS  C                              .
08            AS  C                              .
09            AS  C                    S         .
0a            AS  C                    S         .
0b            AS  C                    S         .
0c            AS  C                    S         .
0d            AS  C                    S         .
0e            AS  C                              .
0f            AS  C                              .
10            AS  C                              .
11            AS  C                              .
12            AS  C                              .
13            AS  C                              .
14            AS  C                              .
15            AS  C                              .
16            AS  C                              .
17            AS  C                              .
18            AS  C                              .
19            AS  C                              .
1a            AS  C                              .
1b            AS  C                              .
1c            AS  C                              .
1d            AS  C                              .
1e            AS  C                              .
1f            AS  C                              .
20            AS                       S PR      .
21   !        AS              G    PU    PR      .
22   "        AS              G    PU    PR      .
23   #        AS              G    PU    PR      .
24   $        AS              G    PU    PR      .
25   %        AS              G    PU    PR      .
26   &        AS              G    PU    PR      .
27   '        AS              G    PU    PR      .
28   (        AS              G    PU    PR      .
29   )        AS              G    PU    PR      .
2a   *        AS              G    PU    PR      .
2b   +        AS              G    PU    PR      .
2c   ,        AS              G    PU    PR      .
2d   -        AS              G    PU    PR      .
2e   .        AS              G    PU    PR      .
2f   /        AS              G    PU    PR      .
30   0  AN    AS   CS      D  G          PR     X.
31   1  AN    AS   CS      D  G          PR     X.
32   2  AN    AS   CS      D  G          PR     X.
33   3  AN    AS   CS      D  G          PR     X.
34   4  AN    AS   CS      D  G          PR     X.
35   5  AN    AS   CS      D  G          PR     X.
36   6  AN    AS   CS      D  G          PR     X.
37   7  AN    AS   CS      D  G          PR     X.
38   8  AN    AS   CS      D  G          PR     X.
39   9  AN    AS   CS      D  G          PR     X.
3a   :        AS              G    PU    PR      .
3b   ;        AS              G    PU    PR      .
3c   <        AS              G    PU    PR      .
3d   =        AS              G    PU    PR      .
3e   >        AS              G    PU    PR      .
3f   ?        AS              G    PU    PR      .
40   @        AS              G    PU    PR      .
41   A  AN  A AS   CS CSF     G          PR  U  X.
42   B  AN  A AS   CS CSF     G          PR  U  X.
43   C  AN  A AS   CS CSF     G          PR  U  X.
44   D  AN  A AS   CS CSF     G          PR  U  X.
45   E  AN  A AS   CS CSF     G          PR  U  X.
46   F  AN  A AS   CS CSF     G          PR  U  X.
47   G  AN  A AS   CS CSF     G          PR  U   .
48   H  AN  A AS   CS CSF     G          PR  U   .
49   I  AN  A AS   CS CSF     G          PR  U   .
4a   J  AN  A AS   CS CSF     G          PR  U   .
4b   K  AN  A AS   CS CSF     G          PR  U   .
4c   L  AN  A AS   CS CSF     G          PR  U   .
4d   M  AN  A AS   CS CSF     G          PR  U   .
4e   N  AN  A AS   CS CSF     G          PR  U   .
4f   O  AN  A AS   CS CSF     G          PR  U   .
50   P  AN  A AS   CS CSF     G          PR  U   .
51   Q  AN  A AS   CS CSF     G          PR  U   .
52   R  AN  A AS   CS CSF     G          PR  U   .
53   S  AN  A AS   CS CSF     G          PR  U   .
54   T  AN  A AS   CS CSF     G          PR  U   .
55   U  AN  A AS   CS CSF     G          PR  U   .
56   V  AN  A AS   CS CSF     G          PR  U   .
57   W  AN  A AS   CS CSF     G          PR  U   .
58   X  AN  A AS   CS CSF     G          PR  U   .
59   Y  AN  A AS   CS CSF     G          PR  U   .
5a   Z  AN  A AS   CS CSF     G          PR  U   .
5b   [        AS              G    PU    PR      .
5c   \        AS              G    PU    PR      .
5d   ]        AS              G    PU    PR      .
5e   ^        AS              G    PU    PR      .
5f   _        AS   CS CSF     G    PU    PR      .
60   `        AS              G    PU    PR      .
61   a  AN  A AS   CS CSF     G  L       PR     X.
62   b  AN  A AS   CS CSF     G  L       PR     X.
63   c  AN  A AS   CS CSF     G  L       PR     X.
64   d  AN  A AS   CS CSF     G  L       PR     X.
65   e  AN  A AS   CS CSF     G  L       PR     X.
66   f  AN  A AS   CS CSF     G  L       PR     X.
67   g  AN  A AS   CS CSF     G  L       PR      .
68   h  AN  A AS   CS CSF     G  L       PR      .
69   i  AN  A AS   CS CSF     G  L       PR      .
6a   j  AN  A AS   CS CSF     G  L       PR      .
6b   k  AN  A AS   CS CSF     G  L       PR      .
6c   l  AN  A AS   CS CSF     G  L       PR      .
6d   m  AN  A AS   CS CSF     G  L       PR      .
6e   n  AN  A AS   CS CSF     G  L       PR      .
6f   o  AN  A AS   CS CSF     G  L       PR      .
70   p  AN  A AS   CS CSF     G  L       PR      .
71   q  AN  A AS   CS CSF     G  L       PR      .
72   r  AN  A AS   CS CSF     G  L       PR      .
73   s  AN  A AS   CS CSF     G  L       PR      .
74   t  AN  A AS   CS CSF     G  L       PR      .
75   u  AN  A AS   CS CSF     G  L       PR      .
76   v  AN  A AS   CS CSF     G  L       PR      .
77   w  AN  A AS   CS CSF     G  L       PR      .
78   x  AN  A AS   CS CSF     G  L       PR      .
79   y  AN  A AS   CS CSF     G  L       PR      .
7a   z  AN  A AS   CS CSF     G  L       PR      .
7b   {        AS              G    PU    PR      .
7c   |        AS              G    PU    PR      .
7d   }        AS              G    PU    PR      .
7e   ~        AS              G    PU    PR      .
7f            AS  C                              .
```

## <a name="see-also"></a>請參閱

[字元分類](../c-runtime-library/character-classification.md)<br/>
[地區設定](../c-runtime-library/locale.md)<br/>
[setlocale、_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[多位元組字元序列的解譯](../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[to 函式](../c-runtime-library/to-functions.md)