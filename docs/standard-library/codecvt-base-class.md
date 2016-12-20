---
title: "codecvt_base 類別 | Microsoft Docs"
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
  - "codecvt_base"
  - "xlocale/std::codecvt_base"
  - "std.codecvt_base"
  - "std::codecvt_base"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "codecvt_base 類別"
ms.assetid: 7e95c083-91b4-4b3f-8918-0d4ea244a040
caps.latest.revision: 21
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# codecvt_base 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

用來定義稱為的列舉型別 **result**的 codecvt 類別的基底類別，使用， Facet 成員的傳回型別函式表示轉換的結果。  
  
## 語法  
  
```  
class codecvt_base : public locale::facet {  
public:  
    enum result {ok, partial, error, noconv};  
    codecvt_base(  
        size_t _Refs = 0  
);  
    bool always_noconv() const;  
    int max_length() const;  
    int encoding() const;  
    ~codecvt_base()  
protected:  
    virtual bool do_always_noconv() const;  
    virtual int do_max_length() const;  
    virtual int do_encoding() const;  
};  
```  
  
## 備註  
 類別會描述列舉通用樣板類別 [codecvt](../standard-library/codecvt-class.md)的所有特製化。  列舉結果描述從 [do\_in](../Topic/codecvt::do_in.md) 或 [do\_out](../Topic/codecvt::do_out.md)的可能傳回值:  
  
-   **ok** ，如果在內部和外部字元編碼之間的轉換成功。  
  
-   **partial** ，如果目的地不夠大才能轉換成功。  
  
-   **error** ，如果來源序列組成錯誤。  
  
-   **noconv** 函式，則不會執行轉換。  
  
## 需求  
 **Header:** \<地區設定\>  
  
 **命名空間:** std  
  
## 請參閱  
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)