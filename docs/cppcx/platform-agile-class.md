---
title: "Platform::Agile 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "agile/Platform::Agile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::Agile"
ms.assetid: e34459a9-c429-4c79-97fd-030c43ca4155
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 4
---
# Platform::Agile 類別
以 Agile 物件來表示具有 MashalingBehavior\=Standard 的物件，可大幅降低發生執行階段執行緒例外狀況的機會。`Agile<T>` 可讓非 Agile 物件呼叫相同或不同的執行緒，或者從中被呼叫。 如需詳細資訊，請參閱[執行緒和封送處理](../cppcx/threading-and-marshaling-c-cx.md)。  
  
## 語法  
  
```scr  
  
template <typename T>  
    class Agile  
;  
```  
  
#### 參數  
 T  
 非 Agile 類別的 typename。  
  
## 備註  
 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] 中的大部分類別都是 Agile。 Agile 物件可以在相同或不同的執行緒中呼叫同處理序或跨處理序物件，或者從中被呼叫。 如果物件不是 Agile，請將非 Agile 物件包裝在 Agile 的 `Agile<T>` 物件中。 這樣就可以封送處理 `Agile<T>` 物件，且可以使用基礎的非 Agile 物件。  
  
 `Agile<T>` 類別是原生、標準 C\+\+ 類別，需要 `agile.h`。 它代表非 Agile 物件和 Agile 物件的*「內容」*\(context\)。 內容指定 Agile 物件的執行緒模型和封送處理行為。 作業系統使用內容來決定如何將物件封送處理。  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[Agile::Agile 建構函式](../cppcx/agile-agile-constructor.md)|初始化 Agile 類別的新執行個體。|  
|[Agile::~Agile 解構函式](../cppcx/agile-tilde-agile-destructor.md)|終結 Agile 類別的目前執行個體。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[Agile::Get](../cppcx/agile-get-method.md)|傳回目前 Agile 物件所代表的物件控制代碼。|  
|[Agile::GetAddressOf](../cppcx/agile-getaddressof-method.md)|重新初始化目前 Agile 物件，然後傳回 `T` 類型物件的控制代碼位址。|  
|[Agile::GetAddressOfForInOut](../cppcx/agile-getaddressofforinout-method.md)|傳回目前 Agile 物件所代表的物件的控制代碼位址。|  
|[Agile::Release](../cppcx/agile-release-method.md)|捨棄目前 Agile 物件的基礎物件和內容。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[Agile::operator\-\>](../cppcx/agile-operator-arrow-operator.md)|擷取目前 Agile 物件所代表的物件控制代碼。|  
|[Agile::operator\=](../cppcx/agile-operator-assign-operator.md)|將指定的值指派給目前 Agile 物件。|  
  
## 繼承階層  
 `Object`  
  
 `Agile`  
  
## 需求  
 **最低支援用戶端：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **最低支援伺服器：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空間：**Platform  
  
 **標頭：**agile.h  
  
## 請參閱  
 [\(NOTINBUILD\) Platform 命名空間](http://msdn.microsoft.com/zh-tw/f3ce3eab-028c-4204-ba9f-9ab8af17c8c4)