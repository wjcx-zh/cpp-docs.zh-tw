---
title: "collate_byname 類別 | Microsoft Docs"
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
  - "std::collate_byname"
  - "locale/std::collate_byname"
  - "std.collate_byname"
  - "collate_byname"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "collate_byname 類別"
ms.assetid: 3dc380df-867c-4763-b60e-ba62a8e63ca7
caps.latest.revision: 24
caps.handback.revision: 24
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# collate_byname 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

衍生的樣板類別，描述可以做為特定地區設定的定序 facet 的物件，啟用有關字串排序慣例的文化特性區域特定資訊的擷取。  
  
## <a name="syntax"></a>語法  
  
```
template <class CharType>
class collate_byname : public collate<CharType> {
public:
    explicit collate_byname(
    const char* _Locname,
    size_t _Refs = 0);

    explicit collate_byname(
    const string& _Locname,
    size_t _Refs = 0);

protected:
    virtual ~collate_byname();

};
```  
  
#### <a name="parameters"></a>參數  
 `_Locname`  
 具名的地區設定。  
  
 `_Refs`  
 初始的參考計數。  
  
## <a name="remarks"></a>備註  
 此樣板類別描述可以做為物件 [地區設定 facet](../standard-library/locale-class.md#facet_class) 型別的 [collate](../standard-library/collate-class.md#collate__collate)\< CharType>。 其行為取決於 [名為](../standard-library/locale-class.md#locale__name) 地區設定 `_Locname`。 每個建構函式初始化具有其基底物件 [collate](../standard-library/collate-class.md#collate__collate)\< CharType>( `_Refs`)。  
  
## <a name="requirements"></a>需求  
 **標頭︰** \< 地區設定>  
  
 **命名空間︰** std  
  
## <a name="see-also"></a>請參閱  
 [C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)



