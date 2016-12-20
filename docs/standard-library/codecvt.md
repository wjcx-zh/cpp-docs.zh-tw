---
title: "&lt; &gt; codecvt | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "codecvt"
  - "std::<codecvt>"
  - "std.<codecvt>"
  - "<codecvt>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "codecvt 標頭"
ms.assetid: d44ee229-00d5-4761-9b48-0c702122789d
caps.latest.revision: 21
caps.handback.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# &lt; &gt; codecvt
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

定義數個範本類別描述範本類別為基礎的物件 [codecvt](../standard-library/codecvt-class.md)。 這些物件可以做為 [的地區設定 facet](../standard-library/locale-class.md#facet_class) 的控制項類型的值序列之間轉換 `Elem` 類型的值序列和 `char`。  
  
## <a name="syntax"></a>語法  
  
```  
#include <codecvt>  
  
```  
  
## <a name="remarks"></a>備註  
 在此標頭中宣告的地區設定 facet 數種字元編碼之間進行轉換。 寬字元 （儲存在固定大小的整數中的程式）︰  
  
-   UCS 4 是在程式內編碼的 Unicode (ISO 10646)  
  
-   Ucs-4 是以 32 位元整數的形式在程式內編碼的 Unicode (ISO 10646)。  
  
-   Ucs-2 是在程式內編碼的 Unicode  
  
-   Ucs-2 是 Unicode 編碼為 16 位元整數的程式中。  
  
-   Utf-16 是做為其中一個程式內編碼的 Unicode  
  
-   Utf-16 是 Unicode 編碼程式中，為一或兩個 16 位元整數。 （請注意這不符合有效寬字元編碼的標準 C 或 Standard c + + 的所有需求。 不過它是廣泛用於這類）。  
  
 位元組資料流 (儲存在檔案、 傳輸的位元組序列，或儲存在陣列中的程式 `char`):  
  
-   Utf-8 是 Unicode 編碼  
  
-   Utf-8 是做為具決定性的位元組順序的一或多個八位元位元組編碼為位元組資料流內的 Unicode。  
  
-   UTF 16LE 是 Unicode 編碼  
  
-   UTF 16LE 是 Unicode 編碼為 utf-16 位元組資料流中的每個 16 位元整數，先顯示以兩個八位元位元組，較大顯著性位元組。  
  
-   UTF 16BE 是 Unicode 編碼  
  
-   UTF 16BE 是 Unicode 編碼為 utf-16 位元組資料流中的每個 16 位元整數，先顯示以兩個八位元位元組，更重要的位元組。  
  
### <a name="enumerations"></a>列舉  
  
|||  
|-|-|  
|[codecvt_mode](../Topic/%3Ccodecvt%3E%20enums.md#codecvt_mode_enumeration)|指定的地區設定 facet 的組態資訊。|  
  
### <a name="classes"></a>類別  
  
|||  
|-|-|  
|[codecvt_utf8](../Topic/%3Ccodecvt%3E%20functions.md#codecvt_utf8)|表示地區設定 facet，寬字元編碼為 ucs-2 或 ucs-4，並以 utf-8 格式編碼的位元組資料流之間進行轉換。|  
|[codecvt_utf8_utf16](%3Ccodecvt%3E%20functions.md#codecvt_utf8_utf16)|表示為 utf-16 編碼的寬字元和以 utf-8 格式編碼的位元組資料流之間進行轉換的地區設定 facet。|  
|[codecvt_utf16](../Topic/%3Ccodecvt%3E%20functions.md#codecvt_utf16)|表示為 ucs-2 或 ucs-4 編碼的寬字元和編碼為 UTF-8 16LE 或 UTF 16BE 位元組資料流之間進行轉換的地區設定 facet。|  
  
## <a name="requirements"></a>需求  
 **標頭︰** \< codecvt>  
  
 **命名空間︰** stdt  
  
## <a name="see-also"></a>請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)




