---
title: "C + + 位元欄位 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- bitfields [C++]
- fields [C++], bit
- bit fields
ms.assetid: 6f4b62e3-cc1d-4e5d-bf34-05904104f71a
caps.latest.revision: 8
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 71f70995cf1a59153a380f0e22f0321fd59abee0
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="c-bit-fields"></a>C++ 位元欄位
類別和結構可包含比整數類型佔用較少儲存區的成員。 這些成員指定為位元欄位。 位元欄位的語法*成員宣告子*規格如下所示：  
  
## <a name="syntax"></a>語法  
  
```  
  
declarator  : constant-expression  
```  
  
## <a name="remarks"></a>備註  
 (選擇性) `declarator` 是在程式中用來存取成員的名稱。 它必須是整數類資料類型 (包括列舉類型)。 *常數運算式*結構中指定的成員所佔用的位元數。 匿名位元欄位 (亦即沒有識別項的位元欄位成員) 可用於填補。  
  
> [!NOTE]
>  未命名且寬度 0 的位元欄位會將下一個位元欄位強制對齊到下一個 `type` 界限，其中 `type` 為成員的類型。  
  
 下列範例宣告包含位元欄位的結構：  
  
```  
// bit_fields1.cpp  
// compile with: /LD  
struct Date {  
   unsigned short nWeekDay  : 3;    // 0..7   (3 bits)  
   unsigned short nMonthDay : 6;    // 0..31  (6 bits)  
   unsigned short nMonth    : 5;    // 0..12  (5 bits)  
   unsigned short nYear     : 8;    // 0..100 (8 bits)  
};  
```  
  
 `Date` 類型物件的概念性記憶體配置如下圖所示。  
  
 ![Date 物件的記憶體配置](../cpp/media/vc38uq1.png "vc38UQ1")  
Date 物件的記憶體配置  
  
 請注意，`nYear`為 8 位元，並會溢位字邊界，宣告的型別，**不帶正負號短**。 因此，它一個新的開頭處開始**不帶正負號短**。 不需要所有位元欄位都調整至基礎類型的一個物件中；新的單位儲存根據宣告所要求的位元數目進行配置。  
  
 **Microsoft 特定的**  
  
 宣告為位元欄位的資料之順序是由低至高位元，如上面的圖所示。  
  
 **END Microsoft 特定的**  
  
 如果結構的宣告包含未命名且長度為 0 的欄位，如下列範例所示：  
  
```  
// bit_fields2.cpp  
// compile with: /LD  
struct Date {  
   unsigned nWeekDay  : 3;    // 0..7   (3 bits)  
   unsigned nMonthDay : 6;    // 0..31  (6 bits)  
   unsigned           : 0;    // Force alignment to next boundary.  
   unsigned nMonth    : 5;    // 0..12  (5 bits)  
   unsigned nYear     : 8;    // 0..100 (8 bits)  
};  
```  
  
 記憶體配置如下圖所示。  
  
 ![具有零 & #45 的 Date 物件配置; 長度位元欄位](../cpp/media/vc38uq2.png "vc38UQ2")  
具有長度為零之位元欄位的 Date 物件配置  
  
 中所述，位元欄位的基礎類型必須是整數類型、[基本類型](../cpp/fundamental-types-cpp.md)。  
  
## <a name="restrictions-on-bit-fields"></a>位元欄位的限制  
 下列清單詳細說明位元欄位的錯誤作業：  
  
1.  取得位元欄位的位址。  
  
2.  使用位元欄位初始化參考。  
  
## <a name="see-also"></a>另請參閱  
 [類別和結構](../cpp/classes-and-structs-cpp.md)
