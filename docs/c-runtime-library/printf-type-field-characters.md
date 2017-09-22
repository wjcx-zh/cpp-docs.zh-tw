---
title: "printf 類型欄位字元 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apilocation: 
  - "msvcr100.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
apitype: "DLLExport"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "printf 函式, 格式規格欄位"
  - "printf 函式, 類型欄位字元"
ms.assetid: 699cb438-cd14-402e-9f81-c7a32acc3317
caps.latest.revision: 15
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# printf 類型欄位字元
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在格式規格中，`type` 字元是轉換規範，其指定對應的引數是否要解譯成字元、字串、指標、整數或浮點數。  `type` 字元是唯一必要的格式規格欄位，會在任何選擇性的欄位之後出現。  
  
 遵循格式字串的引數會根據對應的 `type` 字元和選擇性的[大小](../c-runtime-library/size-specification.md)前置詞解譯。  字元類型 `char` 和 `wchar_t` 的轉換可使用 `c` 或 `C` 來指定，而單一位元組、多位元組或寬字元字串可使用 `s` 或 `S` 來指定，視使用何種格式化函式而定。  使用 `c` 和 `s` 所指定的字元和字串引數會由 `printf` 系列函式解譯為 `char` 和 `char*`，或是由 `wprintf` 系列函式解譯為 `wchar_t` 和 `wchar_t*`。  使用 `C` 和 `S` 所指定的字元和字串引數會由 `printf` 系列函式解譯為 `wchar_t` 和 `wchar_t*`，或是由 `wprintf` 系列函式解譯為 `char` 和 `char*`。  
  
 像是 `short`、`int`、`long`、`long long` 的整數類型和其 `unsigned` 的變化可藉由使用 `d`、`i`、`o`、`u`、`x` 和 `X` 指定。  像是 `float`、`double` 和 `long double` 的浮點類型可藉由使用 `a`、`A`、`e`、`E`、`f`、`g` 和 `G` 指定。  根據預設，除非 `size` 欄位長度前置修改它們，否則會將整數引數強制轉成 `int` 類型，且會將浮點引數強制轉成 `double`。  在 64 位元系統上，`int` 是 32 位元值；因此，除非使用 `ll` 或 `I64` 的 `size` 前置詞，否則 64 位元整數在為了輸出而格式化時會遭到截斷。  由 `p` 指定的指標類型會使用此平台的預設長度。  
  
> [!NOTE]
>  `C`、`S` 和 `Z` 類型字元以及搭配 `printf` 和 `wprintf` 函式使用時的 `c` 和 `s` 類型字元的行為，是 Microsoft 擴充功能，和 ANSI 不相容。  [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 不支援 `F` 類型字元。  
  
### printf 類型欄位字元  
  
|類型字元|引數|輸出格式|  
|----------|--------|----------|  
|`c`|字元|搭配 `printf` 函式使用時，會指定單一位元組字元；搭配 `wprintf` 函式使用時，會指定寬字元。|  
|`C`|字元|搭配 `printf` 函式使用時，會指定寬字元；搭配 `wprintf` 函式使用時，會指定單一位元組字元。|  
|`d`|整數|帶正負號的十進位整數。|  
|`i`|整數|帶正負號的十進位整數。|  
|`o`|整數|不帶正負號的八進位整數。|  
|`u`|整數|不帶正負號的十進位整數。|  
|`x`|整數|不帶正負號的十六進位整數；使用 "abcdef"。|  
|`X`|整數|不帶正負號的十六進位整數；使用 "ABCDEF"。|  
|`e`|浮點|具有 \[ – \]`d`**.**`dddd` e \[*sign*\]`dd[d]` 形式之帶有正負號的值，其中 `d` 是一個十進位數字，`dddd` 是一個或多個十進位數字，`dd[d]` 是兩個或三個十進位數字 \(取決於[輸出格式](../c-runtime-library/set-output-format.md)和該指數的大小\)，且 *sign* 是 \+ 或 –。|  
|`E`|浮點|與 `e` 格式相同，除了由 **E** 而非 **e** 引入該指數以外。|  
|`f`|浮點|具有 \[ – \]`dddd`**.**`dddd` 形式之帶正負號的值，其中 `dddd` 是一個或多個十進位數字。  小數點前面的位數取決於數字的大小，小數點後面的位數則取決於要求的精確度。|  
|`g`|浮點|帶正負號的值會以 `f` 或 `e` 格式顯示，視何種格式對所指定的值和精確度而言較為精簡。  只有在該值的指數小於 –4 或大於等於 `precision` 引數時會使用 `e` 格式。  會截斷尾端的零，僅當一或多個數字位於小數點後面時，才會顯示小數點。|  
|`G`|浮點|與 `g` 格式相同，除了由 **E** 而非 **e** 在適當時引入該指數以外。|  
|`a`|浮點|具有 \[−\]0x*h.hhhh* **p±**`dd` 形式之帶正負號的十六進位雙精確度浮點數值，其中 *h.hhhh* 是該尾數的十六進位數字 \(使用小寫字母\)，且 `dd` 是該指數的一或多個數字。  指定小數點之後位數的精確度。|  
|`A`|浮點|具有 \[−\]0X*h.hhhh* **P±**`dd` 形式之帶正負號的十六進位雙精確度浮點數值，其中 *h.hhhh* 是該尾數的十六進位數字 \(使用大寫字母\)，且 `dd` 是該指數的一或多個數字。  指定小數點之後位數的精確度。|  
|`n`|整數的指標|目前已成功寫入此資料流或緩衝區的字元數。  會將這個值儲存在整數中，該整數的位址會做為引數而受指定。  請參閱本文稍後的〈安全性提示〉。|  
|`p`|指標類型|顯示引數為十六進位數字的位址。|  
|`s`|String|當搭配 `printf` 函式使用時，會指定單一位元組或多位元組字元字串；當搭配 `wprintf` 函式使用時，會指定寬字元字串。  會顯示字元，直到第一個 null 字元或達到 `precision` 值為止。|  
|`S`|String|當搭配 `printf` 函式使用時，會指定寬字元字串；當搭配 `wprintf` 函式使用時，會指定單一位元組或多位元組字元字串。  會顯示字元，直到第一個 null 字元或達到 `precision` 值為止。|  
|`Z`|`ANSI_STRING` 或 `UNICODE_STRING` 結構|當 [ANSI\_STRING](http://msdn.microsoft.com/library/windows/hardware/ff540605.aspx) [UNICODE\_STRING](http://msdn.microsoft.com/library/windows/hardware/ff564879.aspx) 結構的位址做為引數傳遞時，會顯示包含在由該結構的 `Buffer` 欄位指向之緩衝區中的字串。  使用 `w` 的長度修飾詞前置來指定 `UNICODE_STRING` 引數，例如 `%wZ`。  該結構的 `Length` 欄位必須設定為此字串的長度，以位元組為單位。  該結構的 `MaximumLength` 欄位必須設定為此緩衝區的長度，以位元組為單位。<br /><br /> 通常，`Z` 類型字元只在驅動程式偵錯函式中使用，該函式使用像是 `dbgPrint` 和 `kdPrint` 的格式規格。|  
  
 如果對應於浮點轉換規範的引數是無限大、不確定或 NAN，則下表會列出此格式化輸出。  
  
|值|輸出|  
|-------|--------|  
|\+ 無限大|`1.#INF` *random\-digits*|  
|– 無限大|`–1.#INF` *random\-digits*|  
|不確定 \(與無訊息的 NaN 相同\)|*digit* `.#IND` *random\-digits*|  
|NAN|*digit* `.#NAN` *random\-digits*|  
  
> [!NOTE]
>  如果對應到 `%Z` 的引數或對應到 `%s` 或 `%S` 的引數之 `Buffer` 欄位為 null 指標，則會顯示 "\(null\)"。  
  
> [!NOTE]
>  在所有指數格式中，要顯示的指數之預設位數為三。  您可以使用 [\_set\_output\_format](../c-runtime-library/set-output-format.md) 函式，設定顯示的位數為二，但如果指數的大小有所要求，則擴充到三。  
  
> [!IMPORTANT]
>  因為 `%n` 格式本來就不安全，所以根據預設會予以停用。  如果 `%n` 是在格式字串中遇到，則會叫用無效參數處理常式，如[參數驗證](../c-runtime-library/parameter-validation.md)中所述。  若要啟用 `%n` 支援，請參閱 [\_set\_printf\_count\_output](../c-runtime-library/reference/set-printf-count-output.md)。  
  
## 請參閱  
 [printf、\_printf\_l、wprintf、\_wprintf\_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [格式規格語法：printf 和 wprintf 函式](../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)   
 [旗標指示詞](../c-runtime-library/flag-directives.md)   
 [printf 寬度規格](../c-runtime-library/printf-width-specification.md)   
 [精確度規格](../c-runtime-library/precision-specification.md)   
 [大小規格](../c-runtime-library/size-specification.md)   
 [\_set\_output\_format](../c-runtime-library/set-output-format.md)