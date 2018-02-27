---
title: "source_link_manager 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- source_link_manager
- AGENTS/concurrency::source_link_manager
- AGENTS/concurrency::source_link_manager::source_link_manager
- AGENTS/concurrency::source_link_manager::add
- AGENTS/concurrency::source_link_manager::begin
- AGENTS/concurrency::source_link_manager::contains
- AGENTS/concurrency::source_link_manager::count
- AGENTS/concurrency::source_link_manager::reference
- AGENTS/concurrency::source_link_manager::register_target_block
- AGENTS/concurrency::source_link_manager::release
- AGENTS/concurrency::source_link_manager::remove
- AGENTS/concurrency::source_link_manager::set_bound
dev_langs:
- C++
helpviewer_keywords:
- source_link_manager class
ms.assetid: 287487cf-e0fe-4c35-aa3c-24f081d1ddae
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f6368511a7e824e6e1bb69542815fce1e864a964
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="sourcelinkmanager-class"></a>source_link_manager 類別
`source_link_manager` 物件會管理 `ISource` 區塊與傳訊區塊網路的連結。  
  
## <a name="syntax"></a>語法  
  
```
template<class _LinkRegistry>
class source_link_manager;
```  
  
#### <a name="parameters"></a>參數  
 `_LinkRegistry`  
 網路連結登錄中。  
  
## <a name="members"></a>成員  
  
### <a name="public-typedefs"></a>公用 Typedefs  
  
|名稱|描述|  
|----------|-----------------|  
|`const_pointer`|類型，提供的指標`const`中的項目`source_link_manager`物件。|  
|`const_reference`|提供的參考型別`const`項目儲存在`source_link_manager`物件進行讀取和執行 const 作業。|  
|`iterator`|類型，提供迭代器可以讀取或修改任何項目中的`source_link_manager`物件。|  
|`type`|受連結登錄類型`source_link_manager`物件。|  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[source_link_manager](#ctor)|建構 `source_link_manager` 物件。|  
|[~source_link_manager Destructor](#dtor)|終結`source_link_manager`物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[add](#add)|將加入的來源連結`source_link_manager`物件。|  
|[begin](#begin)|傳回迭代器中的第一個項目`source_link_manager`物件。|  
|[contains](#contains)|搜尋`network_link_registry`在這個`source_link_manager`物件指定的區塊。|  
|[count](#count)|計算中連結的區塊數目`source_link_manager`物件。|  
|[reference](#reference)|取得參考上`source_link_manager`物件。|  
|[register_target_block](#register_target_block)|註冊保存此目標區塊`source_link_manager`物件。|  
|[release](#release)|在釋放參考`source_link_manager`物件。|  
|[remove](#remove)|移除連結，以從`source_link_manager`物件。|  
|[set_bound](#set_bound)|設定來源連結，可以新增至這個最大數目`source_link_manager`物件。|  
  
## <a name="remarks"></a>備註  
 目前，來源區塊是計數的參考。 這是包裝函式上`network_link_registry`物件，可讓並行存取的連結，並提供參考透過回呼連結的能力。 訊息區塊 ( `target_block`s 或`propagator_block`s) 應該將這個類別用於其來源連結。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `source_link_manager`  
  
## <a name="requirements"></a>需求  
 **標頭：** agents.h  
  
 **命名空間：** concurrency  
  
##  <a name="add"></a> 新增 

 將加入的來源連結`source_link_manager`物件。  
  
```
void add(_EType _Link);
```  
  
### <a name="parameters"></a>參數  
 `_Link`  
 要加入區塊的指標。  
  
##  <a name="begin"></a> 開始 

 傳回迭代器中的第一個項目`source_link_manager`物件。  
  
```
iterator begin();
```  
  
### <a name="return-value"></a>傳回值  
 迭代器中的第一個項目定址`source_link_manager`物件。  
  
### <a name="remarks"></a>備註  
 迭代器的結束狀態以`NULL`連結。  
  
##  <a name="contains"></a> 包含 

 搜尋`network_link_registry`在這個`source_link_manager`物件指定的區塊。  
  
```
bool contains(_EType _Link);
```  
  
### <a name="parameters"></a>參數  
 `_Link`  
 在搜尋區塊的指標`source_link_manager`物件。  
  
### <a name="return-value"></a>傳回值  
 `true` 如果找不到指定的區塊，`false`否則。  
  
##  <a name="count"></a> 計數 

 計算中連結的區塊數目`source_link_manager`物件。  
  
```
size_t count();
```  
  
### <a name="return-value"></a>傳回值  
 在連結區塊數目`source_link_manager`物件。  
  
##  <a name="reference"></a> 參考 

 取得參考上`source_link_manager`物件。  
  
```
void reference();
```  
  
##  <a name="register_target_block"></a> register_target_block 

 註冊保存此目標區塊`source_link_manager`物件。  
  
```
void register_target_block(_Inout_ ITarget<typename _Block::source_type>* _PTarget);
```  
  
### <a name="parameters"></a>參數  
 `_PTarget`  
 目標區塊保有這`source_link_manager`物件。  
  
##  <a name="release"></a> 發行 

 在釋放參考`source_link_manager`物件。  
  
```
void release();
```  
  
##  <a name="remove"></a> 移除 

 移除連結，以從`source_link_manager`物件。  
  
```
bool remove(_EType _Link);
```  
  
### <a name="parameters"></a>參數  
 `_Link`  
 要移除，如果在區塊的指標找到。  
  
### <a name="return-value"></a>傳回值  
 `true` 如果找到並移除，連結`false`否則。  
  
##  <a name="set_bound"></a> set_bound 

 設定來源連結，可以新增至這個最大數目`source_link_manager`物件。  
  
```
void set_bound(size_t _MaxLinks);
```  
  
### <a name="parameters"></a>參數  
 `_MaxLinks`  
 連結的數目上限。  
  
##  <a name="ctor"></a> source_link_manager 

 建構 `source_link_manager` 物件。  
  
```
source_link_manager();
```  
  
##  <a name="dtor"></a> ~source_link_manager 

 終結`source_link_manager`物件。  
  
```
~source_link_manager();
```  
  
## <a name="see-also"></a>請參閱  
 [concurrency 命名空間](concurrency-namespace.md)   
 [single_link_registry 類別](single-link-registry-class.md)   
 [multi_link_registry 類別](multi-link-registry-class.md)
