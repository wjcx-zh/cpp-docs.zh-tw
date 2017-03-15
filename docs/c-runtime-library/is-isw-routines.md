---
title: "is、isw 常式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apilocation: 
  - "msvcr110_clr0400.dll"
  - "msvcr90.dll"
  - "msvcr80.dll"
  - "msvcr100.dll"
  - "msvcr110.dll"
  - "msvcr120.dll"
apitype: "DLLExport"
f1_keywords: 
  - "isw"
  - "is"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is 常式"
  - "isw 常式"
ms.assetid: 1e171a57-2cde-41f6-a75f-a080fa3c12e5
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# is、isw 常式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

|||  
|-|-|  
|[isalnum、iswalnum、\_isalnum\_l、\_iswalnum\_l](../c-runtime-library/reference/isalnum-iswalnum-isalnum-l-iswalnum-l.md)|[isgraph、iswgraph、\_isgraph\_l、\_iswgraph\_l](../c-runtime-library/reference/isgraph-iswgraph-isgraph-l-iswgraph-l.md)|  
|[isalpha、iswalpha、\_isalpha\_l、\_iswalpha\_l](../c-runtime-library/reference/isalpha-iswalpha-isalpha-l-iswalpha-l.md)|[isleadbyte、\_isleadbyte\_l](../c-runtime-library/reference/isleadbyte-isleadbyte-l.md)|  
|[isascii \_\_isascii、 iswascii](../c-runtime-library/reference/isascii-isascii-iswascii.md)|[islower、iswlower、\_islower\_l、\_iswlower\_l](../c-runtime-library/reference/islower-iswlower-islower-l-iswlower-l.md)|  
|[isblank、iswblank、\_isblank\_l、\_iswblank\_l](../c-runtime-library/reference/isblank-iswblank-isblank-l-iswblank-l.md)|[isprint、iswprint、\_isprint\_l、\_iswprint\_l](../c-runtime-library/reference/isprint-iswprint-isprint-l-iswprint-l.md)|  
|[iscntrl、iswcntrl、\_iscntrl\_l、\_iswcntrl\_l](../c-runtime-library/reference/iscntrl-iswcntrl-iscntrl-l-iswcntrl-l.md)|[ispunct、iswpunct、\_ispunct\_l、\_iswpunct\_l](../c-runtime-library/reference/ispunct-iswpunct-ispunct-l-iswpunct-l.md)|  
|[iscsym、 iscsymf、 \_\_iscsym、 \_\_iswcsym、 \_\_iscsymf、 \_\_iswcsymf、 \_iscsym\_l、 \_iswcsym\_l、 \_iscsymf\_l、 \_iswcsymf\_l](../c-runtime-library/reference/iscsym-functions.md)|[isspace、iswspace、\_isspace\_l、\_iswspace\_l](../c-runtime-library/reference/isspace-iswspace-isspace-l-iswspace-l.md)|  
|[\_isctype、iswctype、\_isctype\_l、\_iswctype\_l](../c-runtime-library/reference/isctype-iswctype-isctype-l-iswctype-l.md)|[isupper、\_isupper\_l、iswupper、\_iswupper\_l](../c-runtime-library/reference/isupper-isupper-l-iswupper-iswupper-l.md)|  
|[isdigit、iswdigit、\_isdigit\_l、\_iswdigit\_l](../c-runtime-library/reference/isdigit-iswdigit-isdigit-l-iswdigit-l.md)|[isxdigit、iswxdigit、\_isxdigit\_l、\_iswxdigit\_l](../c-runtime-library/reference/isxdigit-iswxdigit-isxdigit-l-iswxdigit-l.md)|  
  
## 備註  
 這些行程能測試在特殊情況下的字元。  
  
 **is** 常式產生有意義的結果對於由 \-1 \(`EOF`\) 到 \( **UCHAR\_MAX** 0xFF\)。  必須是引數型別 `int`。  
  
> [!CAUTION]
>  若開頭為 **is**常式，傳遞型別為 `char` 的引數可能會產生無法預期的結果。  一個值大於 0x7F 且型別為 `char` 的 SBCS 或 MBCS 單一位元組字元為負值。  如果傳遞的是 `char`，則編譯器 \(Compiler\) 可能會將該值轉換成帶正負號 \(Signed\) 的 `int` 或帶正負號的 **long**。  這個由編譯器進行 sign\-extended 的值，可能會有未預期的結果。  
  
 **isw** 常式由 \-1 \(**WEOF**\) 到 0xFFFF 會產生不同意義的結果。  **wint\_t** 資料型別在 WCHAR.H 定義為 **unsigned short**;它可以表示所有寬字元或寬字元檔案結尾 \(**WEOF**\) 值。  
  
 輸出值受地區設定的`LC_CTYPE` 分類設定所影響。如需詳細資訊，請參閱 [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) 。  這些函式沒有以 **\_l** 後綴的版本在這些地區相依的行為上使用目前的地區設定，而以**\_l** 後綴版本除了它們會使用傳入的地區設定參數之外運作相同。  
  
 在「C」地區設定， **is** 常式的測試條件如下:  
  
 `isalnum`  
 英數 \(A\-Z、a\-z或 0–9\)。  
  
 `isalpha`  
 字母 \(a\-z、A\-Z\)。  
  
 `__isascii`  
 ASCII 字元 \(0x00 – 0x7F\)。  
  
 `isblank`  
 水平索引標籤或空白字元 \(0x09 或 0x20\)。  
  
 `iscntrl`  
 控制字元 \(0x00 – 0x1F 或 0x7F\)。  
  
 `__iscsym`  
 字母、底線或數字。  
  
 `__iscsymf`  
 字母或底線。  
  
 **isdigit**  
 十進位數字\(0 – 9\)。  
  
 `isgraph`  
 可列印字元以外的空間 \( \)。  
  
 `islower`  
 小寫字母 \(a – z\)。  
  
 `isprint`  
 可列印的字元包括空格 \(0x20 – 0x7E\)。  
  
 `ispunct`  
 標點符號。  
  
 `isspace`  
 空白字元 \(0x09 – 0x0D 或 0x20\)。  
  
 `isupper`  
 大寫字母 \(A – Z\)。  
  
 `isxdigit`  
 十六進位數字 \(A\-F, a\-f, 0\-9\)。  
  
 對於 **isw** 常式，對於指定條件測試的結果與地區設定無關。  **isw** 函式的測試條件如下:  
  
 `iswalnum`  
 `iswalpha` 或 `iswdigit`。  
  
 `iswalpha`  
 任何寬字元的設定一個由實作環境決定 `iswcntrl`、 `iswdigit`、 `iswpunct`或 `iswspace` 都不是非零。  `iswalpha` 傳回非零只有在寬字元 `iswupper` or `iswlower` i為非零。  
  
 `iswascii`  
 ASCII 字元 \(0x0000 – 0x007F\) 的寬字元表示。  
  
 `iswblank`  
 對應於標準空格字元或是一個由實作環境決定設定寬字元 `iswalnum` 是錯誤的寬字元。  標準空白字元是空白 \(L' '\) 和水平索引標籤 \(L'\\t'\)。  
  
 `iswcntrl`  
 控制項寬字元。  
  
 **\_\_iswcsym**  
 **isalnum** 為 true 的任何寬字元或「\_」字元。  
  
 **\_\_iswcsymf**  
 對於`iswalpha` 為 true 的任何寬字元或「\_」字元。  
  
 `iswctype`  
 字元具有 `desc` 引數所指定的屬性。  對於 `iswctype`之 `desc` 引數的每一個有效值，如下表所示，具有對等寬字元分類常式:  
  
 **iswctype 的相等性 \(**   
 ***c, desc* \) 到其他 isw 測試行程**  
  
|*desc* 引數的值|iswctype \( *c， desc* \) 相等|  
|-----------------|---------------------------------|  
|**\_ALPHA**|**iswalpha\(** `c` **\)**|  
|**\_ALPHA** &#124; **\_DIGIT**|**iswalnum\(** `c` **\)**|  
|**\_BLANK**|**iswblank\(** `c` **\)**|  
|**\_CONTROL**|**iswcntrl\(** `c` **\)**|  
|**\_DIGIT**|**iswdigit\(** `c` **\)**|  
|**\_ALPHA** &#124; **\_DIGIT** &#124; **\_PUNCT**|**iswgraph\(** `c` **\)**|  
|**\_LOWER**|**iswlower\(** `c` **\)**|  
|**\_ALPHA** &#124; **\_BLANK** &#124; **\_DIGIT** &#124; **\_PUNCT**|**iswprint\(** `c` **\)**|  
|**\_PUNCT**|**iswpunct\(** `c` **\)**|  
|**\_BLANK**|**iswblank\(** `c` **\)**|  
|**\_SPACE**|**iswspace\(** `c` **\)**|  
|**\_UPPER**|**iswupper\(** `c` **\)**|  
|**\_HEX**|**iswxdigit\(** `c` **\)**|  
  
 `iswdigit`  
 與十進位數值字元對應的寬字元。  
  
 `iswgraph`  
 可列印的寬字元以外的空間寬字元 \(L' '\)。  
  
 `iswlower`  
 小寫字母或一個由實作環境決定 `iswcntrl`、 `iswdigit`、 `iswpunct`或 `iswspace` 都不是非零的設定寬字元。  只有當寬字元對應於小寫字母時，`iswlower` 傳回非零值。  
  
 `iswprint`  
 可列印的寬字元，包含空間寬字元 \(L' '\)。  
  
 `iswpunct`  
 可列印的寬字元不是 \(L' '\) 寬字元也不是 `iswalnum` 為非零值的寬字元。  
  
 `iswspace`  
 對應於標準空格字元或是由實作環境決定設定寬字元 `iswalnum` 是錯誤的寬字元。  標準空白字元如下:空間 \(L' '\)，換頁字元 \(L'\\f'\)，新行字元 \(L'\\n'\)，歸位字元 \(L'\\r'\)，水平索引標籤 \(L'\\t'\) 和垂直索引標籤 \(L'\\v'\)。  
  
 `iswupper`  
 大寫或是一個由實作環境決定設定寬字元 `iswcntrl`、 `iswdigit`、 `iswpunct`或 `iswspace` 都不是非零的寬字元。  只有當寬字元對應於大寫字母時，`iswupper` 傳回非零值。  
  
 `iswxdigit`  
 對應至十六位元字元的寬字元。  
  
## 範例  
  
```  
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
  
## Output  
  
```  
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
  
## 請參閱  
 [字元分類](../c-runtime-library/character-classification.md)   
 [地區設定](../c-runtime-library/locale.md)   
 [setlocale、\_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [多位元組字元序列的解譯](../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [to 函式](../c-runtime-library/to-functions.md)