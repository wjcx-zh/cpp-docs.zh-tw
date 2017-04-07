---
title: "Concurrency:: direct3d 命名空間 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- amp/Concurrency::direct3d
- amprt/Concurrency::direct3d
- amp_short_vectors/Concurrency::direct3d
- amp_graphics/Concurrency::direct3d
- amp_math/Concurrency::direct3d
dev_langs:
- C++
helpviewer_keywords:
- direct3d namespace
ms.assetid: 9566a2f1-4d5f-43e4-a3ac-676643d38420
caps.latest.revision: 15
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
translationtype: Machine Translation
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: 94e0542910484166a01bd79beb9dfaa805aae6cd
ms.lasthandoff: 03/17/2017

---
# <a name="concurrencydirect3d-namespace"></a>Concurrency::direct3d 命名空間
`direct3d`命名空間提供支援 D3D 互通性函式。 它可以順暢地運用 D3D 資源 AMP 程式碼中的計算，以及允許使用所建立的資源 AMP D3D 程式碼中，而不需建立中繼副本。 您可以以累加方式使用 c + + AMP 加速 DirectX 應用程式的計算密集區段並使用 D3D API AMP 計算所產生的資料。  
  
## <a name="syntax"></a>語法  
  
```  
namespace direct3d;  
```  
  
## <a name="members"></a>Members  
  
### <a name="classes"></a>類別  
  
|名稱|描述|  
|----------|-----------------|  
|[scoped_d3d_access_lock 類別](scoped-d3d-access-lock-class.md)|RAII 包裝函式上的 D3D 存取鎖定`accelerator_view`物件。|  
  
### <a name="structures"></a>結構  
  
|名稱|說明|  
|----------|-----------------|  
|[adopt_d3d_access_lock_t 結構](adopt-d3d-access-lock-t-structure.md)|標記類型，以表示 D3D 存取鎖定應該採用，而取得。|  
  
### <a name="functions"></a>函式  
  
|名稱|描述|  
|----------|-----------------|  
|[abs](concurrency-direct3d-namespace-functions-amp.md#abs)|傳回引數的絕對值|  
|[clamp](concurrency-direct3d-namespace-functions-amp.md#clamp)|多載。 鉗制 _X 指定 _Min 和 （_m） 的範圍|  
|[countbits](concurrency-direct3d-namespace-functions-amp.md#countbits)|計算集合中的位元 _X 數目|  
|[create_accelerator_view](concurrency-direct3d-namespace-functions-amp.md#create_accelerator_view)|建立[accelerator_view 類別](accelerator-view-class.md)從 Direct3D 裝置介面的指標|  
|[d3d_access_lock](concurrency-direct3d-namespace-functions-amp.md#d3d_access_lock)|取得 accelerator_view 為了安全地執行 D3D accelerator_view 與共用的資源執行作業的鎖定|  
|[d3d_access_try_lock](concurrency-direct3d-namespace-functions-amp.md#d3d_access_try_lock)|嘗試取得 accelerator_view D3D 存取鎖定，而不會封鎖。|  
|[d3d_access_unlock](concurrency-direct3d-namespace-functions-amp.md#d3d_access_unlock)|釋放指定 accelerator_view D3D 存取鎖定。|  
|[firstbithigh](concurrency-direct3d-namespace-functions-amp.md#firstbithigh)|取得 _X，從最高序位的位元和向下使用中的第一組位元的位置|  
|[firstbitlow](concurrency-direct3d-namespace-functions-amp.md#firstbitlow)|取得 _X，從最低順序位元，且向上運作中的第一組位元的位置|  
|[get_buffer](concurrency-direct3d-namespace-functions-amp.md#get_buffer)|取得基礎陣列 D3D 緩衝區介面。|  
|[imax](concurrency-direct3d-namespace-functions-amp.md#imax)|比較兩個數值，傳回較大的值。|  
|[imin](concurrency-direct3d-namespace-functions-amp.md#imin)|比較兩個數值，傳回較小的值。|  
|[is_timeout_disabled](concurrency-direct3d-namespace-functions-amp.md#is_timeout_disabled)|傳回布林值旗標，表示逾時已停用的指定 accelerator_view。|  
|[mad](concurrency-direct3d-namespace-functions-amp.md#mad)|多載。 執行三個引數的算術/乘積和運算︰ _X * _Y + _Z|  
|[make_array](concurrency-direct3d-namespace-functions-amp.md#make_array)|建立從 D3D 緩衝區介面指標的陣列。|  
|[雜訊](concurrency-direct3d-namespace-functions-amp.md#noise)|藉由使用 Perlin 雜訊演算法產生隨機值|  
|[弧度為單位](concurrency-direct3d-namespace-functions-amp.md#radians)|將 _X 從角度轉換為弧度|  
|[rcp](concurrency-direct3d-namespace-functions-amp.md#rcp)|計算引數的快速、 近似對等|  
|[reversebits](concurrency-direct3d-namespace-functions-amp.md#reversebits)|反轉 _X 的位元的順序|  
|[saturate](concurrency-direct3d-namespace-functions-amp.md#saturate)|鉗制 _X 0 到 1 的範圍內|  
|[符號](concurrency-direct3d-namespace-functions-amp.md#sign)|多載。 傳回引數的符號|  
|[smoothstep](concurrency-direct3d-namespace-functions-amp.md#smoothstep)|介於 0 和 1，傳回的平滑 Hermite 插補，_X 是否在範圍 [_Min，（_m）]。|  
|[步驟](concurrency-direct3d-namespace-functions-amp.md#step)|比較兩個值，傳回 0 或 1 為基礎的值大於|  
|[umax](concurrency-direct3d-namespace-functions-amp.md#umax)|比較兩個不帶正負號的數值，傳回較大的值。|  
|[umin](concurrency-direct3d-namespace-functions-amp.md#umin)|比較兩個不帶正負號的數值，傳回較小的值。|  

## <a name="requirements"></a>需求  
 **標頭︰** amp.h  
  
 **命名空間：** 並行  
  
## <a name="see-also"></a>另請參閱  
 [Concurrency 命名空間 (C++ AMP)](concurrency-namespace-cpp-amp.md)

