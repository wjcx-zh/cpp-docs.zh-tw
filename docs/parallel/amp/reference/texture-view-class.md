---
title: "texture_view 類別 | Microsoft Docs"
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
ms.assetid: 6ec2e289-1626-4727-9592-07981cf1d27d
caps.latest.revision: 11
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# texture_view 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

提供材質的讀取存取和寫入存取。  `texture_view` 只能用於讀取具有預設 32 位元 bpse 且實值類型為 `int`、`unsigned int` 或 `float` 的材質。  若要讀取其他紋理格式，請使用 `texture_view<const _Value_type, _Rank>`。  
  
## 語法  
  
```  
template <  
   typename _Value_type,  
   int _Rank  
>  
class texture_view;  
  
template <  
   typename _Value_type,  
   int _Rank  
>  
class texture_view : public details::_Texture_base<_Value_type, _Rank>;  
  
template <  
   typename _Value_type,  
   int _Rank  
>  
class texture_view<const _Value_type, _Rank> : public details::_Texture_base<_Value_type, _Rank>;  
```  
  
#### 參數  
 `_Value_type`  
 材質彙總中項目的類型。  
  
 `_Rank`  
 `texture_view` 的順位。  
  
## Members  
  
### 公用 Typedefs  
  
|名稱|描述|  
|--------|--------|  
|`value_type`|材質彙總中項目的類型。|  
|`coordinates_type`|用於指定 `texture_view` 中之材質的座標類型，也就是其陣序和實值類型為 `float` 之關聯材質相同的 `short_vector`。|  
|`gather_return_type`|用於收集作業的傳回類型，也就是陣序為 4 的 `short_vector`，其保存從四個取樣材質值收集的四個同質色彩元件。|  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[texture\_view::texture\_view 建構函式](../Topic/texture_view::texture_view%20Constructor.md)|多載。  建構 `texture_view` 執行個體。|  
|[texture\_view::~texture\_view 解構函式](../Topic/texture_view::~texture_view%20Destructor.md)|終結 `texture_view` 執行個體。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[texture\_view::gather\_alpha 方法](../Topic/texture_view::gather_alpha%20Method.md)|多載。  使用指定的取樣組態，在指定的座標對材質進行取樣，並傳回四個取樣材質的 Alpha \(w\) 元件。|  
|[texture\_view::gather\_blue 方法](../Topic/texture_view::gather_blue%20Method.md)|多載。  使用指定的取樣組態，在指定的座標對材質進行取樣，並傳回四個取樣材質的藍色 \(z\) 元件。|  
|[texture\_view::gather\_green 方法](../Topic/texture_view::gather_green%20Method.md)|多載。  使用指定的取樣組態，在指定的座標對材質進行取樣，並傳回四個取樣材質的綠色 \(y\) 元件。|  
|[texture\_view::gather\_red 方法](../Topic/texture_view::gather_red%20Method.md)|多載。  使用指定的取樣組態，在指定的座標對材質進行取樣，並傳回四個取樣材質的紅色 \(x\) 元件。|  
|[texture\_view::get 方法](../Topic/texture_view::get%20Method.md)|多載。  依據索引取得項目值。|  
|[texture\_view::sample 方法](../Topic/texture_view::sample%20Method.md)|多載。  使用指定的取樣組態，在指定的座標和詳細資料層級對材質進行取樣。|  
|[texture\_view::set 方法](../Topic/texture_view::set%20Method.md)|依索引設定元素的值。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[texture\_view::operator\(\) 運算子](../Topic/texture_view::operator\(\)%20Operator.md)|多載。  依據索引取得項目值。|  
|[texture\_view::operatorOperator](../Topic/texture_view::operatorOperator.md)|多載。  依據索引取得項目值。|  
|[texture\_view::operator\= 運算子](../Topic/texture_view::operator=%20Operator.md)|多載。  指派運算子。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[texture\_view::value\_type 資料成員](../Topic/texture_view::value_type%20Data%20Member.md)|`texture_view` 中項目的實值類型。|  
  
## 繼承階層架構  
 `_Texture_base`  
  
 `texture_view`  
  
## 需求  
 **標頭：**amp\_graphics.h  
  
 **命名空間：**concurrency::graphics  
  
## 請參閱  
 [Concurrency::graphics 命名空間](../../../parallel/amp/reference/concurrency-graphics-namespace.md)