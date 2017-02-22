---
title: "wstring_convert 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cvt.wstring_convert"
  - "wstring_convert"
  - "stdext::cvt::wstring_convert"
  - "cvt::wstring_convert"
  - "wstring/stdext::cvt::wstring_convert"
  - "stdext.cvt.wstring_convert"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "wstring_convert 類別"
ms.assetid: e34f5b65-d572-4bdc-ac69-20778712e376
caps.latest.revision: 25
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 25
---
# wstring_convert 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

範本類別 `wstring_convert` 會執行寬字串與位元組字串之間的轉換。  
  
## 語法  
  
```  
template<  
    class Codecvt,  
    class Elem = wchar_t  
>  
class wstring_convert  
```  
  
#### 參數  
 Codecvt  
 表示轉換物件的[地區設定](../standard-library/locale-class.md) facet。  
  
 Elem  
 寬字元項目類型。  
  
## 備註  
 此範本類別會說明對類別 `std::basic_string<Elem>` 的寬字串物件與類別 `std::basic_string<char>` \(也稱為 `std::string`\) 的位元組字串物件之間的轉換進行控制的物件。 此範本類別會將類型 `wide_string` 和 `byte_string` 定義為這兩種類型的同義字。`Elem` 值的序列 \(儲存在 `wide_string` 物件中\) 與多位元組序列 \(儲存在 `byte_string` 物件中\) 之間的轉換，是由類別 `Codecvt<Elem, char, std::mbstate_t>` 的物件所執行，其符合標準程式碼轉換 facet `std::codecvt<Elem, char, std::mbstate_t>` 的需求。  
  
 此樣板類別的物件會儲存：  
  
-   發生錯誤時顯示的位元組字串  
  
-   發生錯誤時顯示的寬字串  
  
-   配置的轉換物件的指標 \(在終結 wbuffer\_convert 物件時釋放\)  
  
-   類型 [state\_type](../Topic/wstring_convert::state_type.md) 的轉換狀態物件  
  
-   轉換計數  
  
### 建構函式  
  
|||  
|-|-|  
|[wstring\_convert](../Topic/wstring_convert::wstring_convert.md)|建構類型 `wstring_convert` 的物件。|  
  
### Typedefs  
  
|||  
|-|-|  
|[byte\_string](../Topic/wstring_convert::byte_string.md)|代表位元組字串的類型。|  
|[wide\_string](../Topic/wstring_convert::wide_string.md)|代表寬字串的類型。|  
|[state\_type](../Topic/wstring_convert::state_type.md)|代表轉換狀態的類型。|  
|[int\_type](../Topic/wstring_convert::int_type.md)|代表整數的類型。|  
  
### 成員函式  
  
|||  
|-|-|  
|[from\_bytes](../Topic/wstring_convert::from_bytes.md)|將位元組字串轉換為寬字串。|  
|[to\_bytes](../Topic/wstring_convert::to_bytes.md)|將寬字串轉換為位元組字串。|  
|[已轉換](../Topic/wstring_convert::converted.md)|傳回成功轉換的數目。|  
|[狀態](../Topic/wstring_convert::state.md)|傳回表示轉換狀態的物件。|  
  
## 需求  
 **標頭：**\<locale\>  
  
 **命名空間:** std