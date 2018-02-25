---
title: "wbuffer_convert 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- xlocmon/stdext::cvt::wbuffer_convert
dev_langs:
- C++
helpviewer_keywords:
- wbuffer_convert class
ms.assetid: 4a56f9bf-4138-4612-b516-525fea401358
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e0153bf7d40dbd4290900d15b6e68d84d0c07869
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="wbufferconvert-class"></a>wbuffer_convert 類別
描述資料流緩衝區，可控制與位元組資料流緩衝區之間的項目傳輸。  
  
## <a name="syntax"></a>語法  
  
```
template <class Codecvt, class Elem = wchar_t, class Traits = std::char_traits<Elem>>
class wbuffer_convert
 : public std::basic_streambuf<Elem, Traits>
```  
  
#### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|`Codecvt`|[locale](../standard-library/locale-class.md) Facet，代表轉換物件。|  
|`Elem`|寬字元項目類型。|  
|`Traits`|與 *Elem* 相關聯的特性。|  
  
## <a name="remarks"></a>備註  
 此範本類別描述資料流緩衝區，可控制類型 `_Elem` (其字元特性由類別 `Traits` 所描述) 的項目，與類型 `std::streambuf` 的位元組資料流緩衝區之間的傳輸。  
  
 `Elem` 值序列與多位元組序列之間的轉換，是由類別 `Codecvt<Elem, char, std::mbstate_t>` 的物件所執行，其符合標準程式碼轉換 facet `std::codecvt<Elem, char, std::mbstate_t>` 的需求。  
  
 此樣板類別的物件會儲存：  
  
-   其基礎位元組資料流緩衝區的指標  
  
-   配置的轉換物件的指標 (在終結 [wbuffer_convert](../standard-library/wbuffer-convert-class.md) 物件時釋放)
