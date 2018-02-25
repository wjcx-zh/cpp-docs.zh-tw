---
title: "Concurrency:: direct3d 命名空間 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 607a3f25c2dfea5eee833f3608021547d8cd7c44
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="concurrencydirect3d-namespace"></a>Concurrency::direct3d 命名空間
`direct3d`命名空間提供支援 D3D 互通性函式。 它可讓您順暢使用 D3D 資源 AMP 程式碼中的計算，以及允許在 AMP 建立 D3D 程式碼中，而不需要建立重複的中繼複本的資源使用。 您可以逐步進行加速使用 c + + AMP 計算密集區段 DirectX 應用程式，並從 AMP 計算所產生的資料上使用 D3D API。  
  
## <a name="syntax"></a>語法  
  
```  
namespace direct3d;  
```  
  
## <a name="members"></a>成員  
  
### <a name="classes"></a>類別  
  
|名稱|描述|  
|----------|-----------------|  
|[scoped_d3d_access_lock 類別](scoped-d3d-access-lock-class.md)|RAII 包裝函式上的 D3D 存取鎖定`accelerator_view`物件。|  
  
### <a name="structures"></a>結構  
  
|名稱|描述|  
|----------|-----------------|  
|[adopt_d3d_access_lock_t 結構](adopt-d3d-access-lock-t-structure.md)|標記型別以表示 D3D 存取鎖定應該採用而取得。|  
  
### <a name="functions"></a>函式  
  
|名稱|描述|  
|----------|-----------------|  
|[abs](concurrency-direct3d-namespace-functions-amp.md#abs)|傳回引數的絕對值|  
|[clamp](concurrency-direct3d-namespace-functions-amp.md#clamp)|多載。 強加 _X 指定 _Min 和 （_m） 的範圍|  
|[countbits](concurrency-direct3d-namespace-functions-amp.md#countbits)|計算集合中的位元 _X 數目|  
|[create_accelerator_view](concurrency-direct3d-namespace-functions-amp.md#create_accelerator_view)|建立[accelerator_view 類別](accelerator-view-class.md)從 Direct3D 裝置介面的指標|  
|[d3d_access_lock](concurrency-direct3d-namespace-functions-amp.md#d3d_access_lock)|取得 accelerator_view，為了安全地 D3D 上執行的作業與 accelerator_view 共用資源的鎖定|  
|[d3d_access_try_lock](concurrency-direct3d-namespace-functions-amp.md#d3d_access_try_lock)|嘗試取得 accelerator_view D3D 存取鎖定，而不會封鎖。|  
|[d3d_access_unlock](concurrency-direct3d-namespace-functions-amp.md#d3d_access_unlock)|釋放指定 accelerator_view 的 D3D 存取鎖定。|  
|[firstbithigh](concurrency-direct3d-namespace-functions-amp.md#firstbithigh)|取得 _X，從最高序位位元，且向下使用中的第一組位元的位置|  
|[firstbitlow](concurrency-direct3d-namespace-functions-amp.md#firstbitlow)|取得 _X，從最低順序位元，且使用向上中的第一組位元的位置|  
|[get_buffer](concurrency-direct3d-namespace-functions-amp.md#get_buffer)|取得基礎陣列 D3D 緩衝區介面。|  
|[imax](concurrency-direct3d-namespace-functions-amp.md#imax)|比較兩個數值，傳回較大的值。|  
|[imin](concurrency-direct3d-namespace-functions-amp.md#imin)|比較兩個數值，傳回較小的值。|  
|[is_timeout_disabled](concurrency-direct3d-namespace-functions-amp.md#is_timeout_disabled)|傳回布林值旗標，指出是否停用的指定 accelerator_view 的逾時。|  
|[mad](concurrency-direct3d-namespace-functions-amp.md#mad)|多載。 執行三個引數的算術的乘/加入運算： _X * 平均數 + _Z|  
|[make_array](concurrency-direct3d-namespace-functions-amp.md#make_array)|建立從 D3D 緩衝區介面指標的陣列。|  
|[noise](concurrency-direct3d-namespace-functions-amp.md#noise)|藉由使用 Perlin 雜訊演算法產生隨機的值|  
|[弧度為單位](concurrency-direct3d-namespace-functions-amp.md#radians)|將 _X 從角度轉換成弧度|  
|[rcp](concurrency-direct3d-namespace-functions-amp.md#rcp)|計算引數的快速、 近似倒數|  
|[reversebits](concurrency-direct3d-namespace-functions-amp.md#reversebits)|反轉 _X 的位元的順序|  
|[saturate](concurrency-direct3d-namespace-functions-amp.md#saturate)|強加 _X 0 到 1 的範圍內|  
|[sign](concurrency-direct3d-namespace-functions-amp.md#sign)|多載。 傳回引數的符號|  
|[smoothstep](concurrency-direct3d-namespace-functions-amp.md#smoothstep)|介於 0 和 1，傳回的 smooth Hermite 插補，_X 是否在範圍 [_Min，（_m）]。|  
|[step](concurrency-direct3d-namespace-functions-amp.md#step)|比較兩個值，傳回 0 或 1 為基礎的值大於|  
|[umax](concurrency-direct3d-namespace-functions-amp.md#umax)|比較兩個不帶正負號的數值，傳回較大的值。|  
|[umin](concurrency-direct3d-namespace-functions-amp.md#umin)|比較兩個不帶正負號的數值，傳回較小的值。|  

## <a name="requirements"></a>需求  
 **標頭︰** amp.h  
  
 **命名空間：** 並行  
  
## <a name="see-also"></a>請參閱  
 [Concurrency 命名空間 (C++ AMP)](concurrency-namespace-cpp-amp.md)
