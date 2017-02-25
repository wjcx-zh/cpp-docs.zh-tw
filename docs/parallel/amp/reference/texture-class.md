---
title: "texture 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "amp_graphics/Concurrency::graphics::texture"
dev_langs: 
  - "C++"
ms.assetid: 16e85d4d-e80a-474a-995d-8bf63fbdf34c
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# texture 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

材質是位在範圍定義域內 `accelerator_view` 上的資料彙總。  它是變數集合，對應範圍網域中的每個項目。  每個變數都會保留對應到 C\+\+ 基本類型 \(`unsigned int`、`int`、`float`、`double`\)、純量類型 \(`norm` 或 `unorm`\) 或短向量類型的值。  
  
## 語法  
  
```  
template <  
   typename _Value_type,  
   int _Rank  
>  
class texture;  
```  
  
#### 參數  
 `_Value_type`  
 材質中項目的類型。  
  
 `_Rank`  
 材質的順位。  
  
## Members  
  
### 公用 Typedefs  
  
|名稱|描述|  
|--------|--------|  
|`scalar_type`|純量類型。|  
|`value_type`|實值類型。|  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[texture::texture 解構函式](../Topic/texture::texture%20Constructor.md)|初始化 [texture](../../../parallel/amp/reference/texture-class.md) 類別的新執行個體。|  
|[texture::~texture 解構函式](../Topic/texture::~texture%20Destructor.md)|終結 [texture](../../../parallel/amp/reference/texture-class.md) 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[texture::copy\_to 方法](../Topic/texture::copy_to%20Method.md)|透過深層複製，將 [texture](../../../parallel/amp/reference/texture-class.md) 物件複製到目的端。|  
|[texture::data 方法](../Topic/texture::data%20Method.md)|傳回此材質原始資料的 CPU 指標。|  
|[texture::get 方法](../Topic/texture::get%20Method.md)|傳回指定索引的項目的值。|  
|[texture::get\_associated\_accelerator\_view 方法](../Topic/texture::get_associated_accelerator_view%20Method.md)|傳回 [accelerator\_view](../../../parallel/amp/reference/accelerator-view-class.md)，也就是此材質的慣用複製目標。|  
|[texture::get\_depth\_pitch 方法](../Topic/texture::get_depth_pitch%20Method.md)|傳回在 CPU 上的 3D 預備環境材質中，每個深度切割之間的位元組數目。|  
|[texture::get\_row\_pitch 方法](../Topic/texture::get_row_pitch%20Method.md)|傳回在 CPU 上的 2D 或 3D 預備環境材質中，每一列之間的位元組數目。|  
|[texture::set 方法](../Topic/texture::set%20Method.md)|設定位於指定索引處的元素值。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[texture::operator\(\) 運算子](../Topic/texture::operator\(\)%20Operator.md)|傳回參數指定的項目值。|  
|[texture::operatorOperator](../Topic/texture::operatorOperator.md)|傳回位在指定索引的項目。|  
|[texture::operator\= 運算子](../Topic/texture::operator=%20Operator.md)|將指定的 [texture](../../../parallel/amp/reference/texture-class.md) 物件複製到這個物件。|  
  
### 公用常數  
  
|名稱|描述|  
|--------|--------|  
|[texture::rank 常數](../Topic/texture::rank%20Constant.md)|取得 [texture](../../../parallel/amp/reference/texture-class.md) 物件的陣序。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[texture::associated\_accelerator\_view 資料成員](../Topic/texture::associated_accelerator_view%20Data%20Member.md)|取得 [accelerator\_view](../../../parallel/amp/reference/accelerator-view-class.md)，也就是此材質的慣用複製目標。|  
|[texture::depth\_pitch 資料成員](../Topic/texture::depth_pitch%20Data%20Member.md)|取得在 CPU 上的 3D 預備環境材質中，每個深度切割之間的位元組數目。|  
|[texture::row\_pitch 資料成員](../Topic/texture::row_pitch%20Data%20Member.md)|取得在 CPU 上的 2D 或 3D 預備環境材質中，每一列之間的位元組數目。|  
  
## 繼承階層架構  
 `_Texture_base`  
  
 `texture`  
  
## 需求  
 **標頭：**amp\_graphics.h  
  
 **命名空間：**Concurrency::graphics  
  
## 請參閱  
 [Concurrency::graphics 命名空間](../../../parallel/amp/reference/concurrency-graphics-namespace.md)