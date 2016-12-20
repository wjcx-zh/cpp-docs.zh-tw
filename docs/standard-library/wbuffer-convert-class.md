---
title: "wbuffer_convert 類別 | Microsoft Docs"
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
  - "stdext::cvt::wbuffer_convert"
  - "wbuffer_convert"
  - "stdext.cvt.wbuffer_convert"
  - "cvt.wbuffer_convert"
  - "cvt::wbuffer_convert"
  - "wbuffer/stdext::cvt::wbuffer_convert"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "wbuffer_convert 類別"
ms.assetid: 4a56f9bf-4138-4612-b516-525fea401358
caps.latest.revision: 20
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# wbuffer_convert 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述資料流緩衝區，可控制與位元組資料流緩衝區之間的項目傳輸。  
  
## 語法  
  
```  
template<class Codecvt,  
    class Elem = wchar_t,  
    class Traits = std::char_traits<Elem>  
>  
    class wbuffer_convert  
        : public std::basic_streambuf<Elem, Traits>  
```  
  
#### 參數  
  
|參數|描述|  
|--------|--------|  
|`Codecvt`|表示轉換物件的[地區設定](../standard-library/locale-class.md) facet。|  
|`Elem`|寬字元項目類型。|  
|`Traits`|與 *Elem* 相關聯的特性。|  
  
## 備註  
 此範本類別描述資料流緩衝區，可控制類型 `_Elem` \(其字元特性由類別 `Traits` 所描述\) 的項目，與類型 `std::streambuf` 的位元組資料流緩衝區之間的傳輸。  
  
 `Elem` 值序列與多位元組序列之間的轉換，是由類別 `Codecvt<Elem, char, std::mbstate_t>` 的物件所執行，其符合標準程式碼轉換 facet `std::codecvt<Elem, char, std::mbstate_t>` 的需求。  
  
 此樣板類別的物件會儲存：  
  
-   其基礎位元組資料流緩衝區的指標  
  
-   配置的轉換物件的指標 \(在終結 [wbuffer\_convert](../standard-library/wbuffer-convert-class.md) 物件時釋放\)  
  
-   類型 [state\_type](../Topic/wbuffer_convert::state_type.md) 的轉換狀態物件。  
  
### 建構函式  
  
|||  
|-|-|  
|[wbuffer\_convert](../Topic/wbuffer_convert::wbuffer_convert.md)|建構類型 `wbuffer_convert` 的物件。|  
  
### Typedefs  
  
|||  
|-|-|  
|[state\_type](../Topic/wbuffer_convert::state_type.md)|代表轉換狀態的類型。|  
  
### 成員函式  
  
|||  
|-|-|  
|[rdbuf](../Topic/wbuffer_convert::rdbuf.md)|傳回位元組資料流緩衝區。|  
|[狀態](../Topic/wbuffer_convert::state.md)|傳回表示轉換狀態的物件。|  
  
## 需求  
 **標頭：**\<locale\>  
  
 **命名空間:** std