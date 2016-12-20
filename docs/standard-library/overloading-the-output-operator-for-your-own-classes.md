---
title: "為您的自訂類別多載 &lt;&lt; 運算子 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "運算子 <<, 為您的自訂類別多載"
  - "operator<<, 為您的自訂類別多載"
ms.assetid: ad1d2c49-d84e-48a8-9c09-121f28b10bf0
caps.latest.revision: 12
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 為您的自訂類別多載 &lt;&lt; 運算子
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

輸出資料流為標準型別使用插入 \(`<<`\) 運算子。  您也可以多載您的類別中的 `<<` 運算子。  
  
## 範例  
 `write` 函式範例示範了使用 `Date` 結構。  日期是資料成員的 C \+\+. 類別的一個理想候選 \(月、日和年\) 從檢視隱藏。  輸出資料流時顯示這類結構邏輯目的地。  使用 `cout` 物件，這個程式碼會顯示日期:  
  
```  
Date dt( 1, 2, 92 );  
cout << dt;  
```  
  
 要取得 `cout` 在插入運算子後面接受 `Date` 物件中，多載插入運算子辨識左邊和 `Date` 的 `ostream` 物件在右邊。  接著必須宣告多載 `<<` 運算子函式，類別 `Date` ，因此它的 friend 可以存取在 `Date` 物件中的私用資料。  
  
```  
// overload_date.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
class Date  
{  
    int mo, da, yr;  
public:  
    Date(int m, int d, int y)  
    {  
        mo = m; da = d; yr = y;  
    }  
    friend ostream& operator<<(ostream& os, const Date& dt);  
};  
  
ostream& operator<<(ostream& os, const Date& dt)  
{  
    os << dt.mo << '/' << dt.da << '/' << dt.yr;  
    return os;  
}  
  
int main()  
{  
    Date dt(5, 6, 92);  
    cout << dt;  
}  
```  
  
  **5\/6\/92**   
## 備註  
 多載運算子會傳回至原始 `ostream` 物件的參考，這表示您可以合併插入:  
  
```  
cout << "The date is" << dt << flush;  
```  
  
## 請參閱  
 [輸出資料流](../standard-library/output-streams.md)