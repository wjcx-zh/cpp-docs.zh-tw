---
title: "大小規格 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apilocation: 
  - "msvcr120.dll"
  - "msvcr80.dll"
  - "msvcr110.dll"
  - "msvcr90.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr100.dll"
apitype: "DLLExport"
f1_keywords: 
  - "size"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "printf 函式, 格式規格欄位"
ms.assetid: 525dc5d8-e70a-4797-a6a0-ec504a27355c
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 14
---
# 大小規格
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在格式規格中，第四個欄位是轉換規範的引數長度修飾詞。  `type` 欄位的 `size` 欄位前置詞 \(`h`、`l`、`w`、`I`、`I32`、`I64` 和 `ll`\) 會根據所修改的轉換規範，來指定對應引數的「大小」：長或短，32 位元或 64 位元、單一位元組字元或寬字元。  這些大小前置詞可在 `printf` 和 `wprintf` 系列函式中搭配 `type` 字元使用，以指定引數長度的轉譯，如下表所示。  `size` 對於某些引數類型是選擇性欄位。  未指定大小前置詞時，格式子會使用整數引數 \(例如帶正負號或不帶正負號的 `char`、`short`、`int`、`long` 和列舉類型\) 做為 32 位元 `int` 類型，並使用浮點引數做為 64 位元 `double` 類型。  這符合變數引數清單的預設引數提升規則。  如需引數提升的詳細資訊，請參閱[省略符號和預設引數](../misc/ellipses-and-default-arguments.md)。  在 32 位元和 64 位元系統上，64 位元整數引數的格式規格必須包含大小前置詞 `ll` 或 `I64`。  否則，格式子的行為未定義。  
  
 某些類型在 32 位元和 64 位元程式碼中的大小不同。  例如，`size_t` 在針對 x86 所編譯的程式碼中的長度為 32 位元，在針對 x64 所編譯的程式碼中的長度為 64 位元。  若要針對變動寬度類型建立無從驗證平台的格式化程式碼，您可以使用變動寬度的引數長度修飾詞。  您也可以使用 64 位元引數長度修飾詞，並明確地將變動寬度的引數類型提升為 64 位元。  Microsoft 特定的 `I` 引數長度修飾詞會處理變動寬度的整數引數。  
  
> [!NOTE]
>  `I`、`I32` 和 `I64` 長度修飾詞的前置詞是 Microsoft 擴充功能，與 ANSI 不相容。  `h` 前置詞可搭配 `char` 類型的資料使用，`w` 前置詞可搭配 `wchar_t` 類型的資料使用，而 `l` 前置詞可搭配 `double` 類型的資料使用，這些前置詞都是 Microsoft 擴充功能。  不支援 `hh`、`j`、`z` 和 `t` 長度前置詞。  
  
### printf 和 wprintf 格式類型規範的大小前置詞  
  
|若要指定|使用前置詞|類型規範為|  
|----------|-----------|-----------|  
|`long int`|`l` \(小寫 L\)|`d`、`i`、`o`、`x` 或 `X`|  
|`long unsigned int`|`l`|`o`、`u`、`x` 或 `X`|  
|`long long`|`ll`|`d`、`i`、`o`、`x` 或 `X`|  
|`short int`|`h`|`d`、`i`、`o`、`x` 或 `X`|  
|`short unsigned int`|`h`|`o`、`u`、`x` 或 `X`|  
|`__int32`|`I32`|`d`、`i`、`o`、`x` 或 `X`|  
|`unsigned __int32`|`I32`|`o`、`u`、`x` 或 `X`|  
|`__int64`|`I64`|`d`、`i`、`o`、`x` 或 `X`|  
|`unsigned __int64`|`I64`|`o`、`u`、`x` 或 `X`|  
|`ptrdiff_t` \(也就是 32 位元平台上的 `__int32` 和 64 位元平台上的 `__int64`\)|`I`|`d`、`i`、`o`、`x` 或 `X`|  
|`size_t` \(也就是 32 位元平台上的 `unsigned __int32` 和 64 位元平台上的 `unsigned __int64`\)|`I`|`o`、`u`、`x` 或 `X`|  
|`long double` \(在 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 中，`long double` 與 `double` 雖然類型不同，但具有相同的內部代碼\)。|`l` 或 `L`|`a`、`A`、`e`、`E`、`f`、`g` 或 `G`。|  
|單一位元組字元搭配 `printf` 和 `wprintf` 函式。  \(`hc` 或 `hC` 類型規範，與 `printf` 函式中的 `c` 和 `wprintf` 函式中的 `C` 同義\)。|`h`|`c` 或 `C`|  
|寬字元搭配 `printf` 和 `wprintf` 函式。  \(`lc`、`lC`、`wc` 或 `wC` 類型規範，與 `printf` 函式中的 `C` 和 `wprintf` 函式中的 `c` 同義\)。|`l` 或 `w`|`c` 或 `C`|  
|單一位元組字元字串搭配 `printf` 和 `wprintf` 函式。  \(`hs` 或 `hS` 類型規範，與 `printf` 函式中的 `s` 和 `wprintf` 函式中的 `S` 同義\)。|`h`|`s`、`S` 或 `Z`|  
|寬字元字串搭配 `printf` 和 `wprintf` 函式。  \(`ls`、`lS`、`ws` 或 `wS` 類型規範，與 `printf` 函式中的 `S` 和 `wprintf` 函式中的 `s` 同義\)。|`l` 或 `w`|`s`、`S` 或 `Z`|  
  
## 請參閱  
 [printf、\_printf\_l、wprintf、\_wprintf\_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [格式規格語法：printf 和 wprintf 函式](../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)   
 [旗標指示詞](../c-runtime-library/flag-directives.md)   
 [printf 寬度規格](../c-runtime-library/printf-width-specification.md)   
 [精確度規格](../c-runtime-library/precision-specification.md)   
 [printf 類型欄位字元](../c-runtime-library/printf-type-field-characters.md)