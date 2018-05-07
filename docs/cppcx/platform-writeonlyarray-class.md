---
title: 'Platform:: writeonlyarray 類別 |Microsoft 文件'
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::WriteOnlyArray::begin
- VCCORLIB/Platform::WriteOnlyArray::Data
- VCCORLIB/Platform::WriteOnlyArray::end
- VCCORLIB/Platform::WriteOnlyArray::FastPass
- VCCORLIB/Platform::WriteOnlyArray::Length
- VCCORLIB/Platform::WriteOnlyArray::set
dev_langs:
- C++
helpviewer_keywords:
- Platform::WriteOnlyArray Class
ms.assetid: 92d7dd56-ec58-4b8c-88ba-9c903668b687
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8f5c1f1f0260d4f1d1c4a6fb640b7cbf1e9d3f2f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="platformwriteonlyarray-class"></a>Platform::WriteOnlyArray 類別
表示一維陣列。當呼叫端傳遞陣列讓方法填滿其中元素時，就會將這個陣列當做輸入參數來傳遞。  
  
 這個 ref 類別在 vccorlib.h 中是宣告為私用，因此不會在中繼資料內發出，而且只能從 C++ 使用。 這個類別只做為用來接收呼叫端所配置之陣列的輸入參數。 您無法從使用者程式碼建構這個類別。 它可以讓 C++ 方法直接在陣列中寫入資料，這就稱為「 *FillArray* 」模式。 如需詳細資訊，請參閱[Array 和 WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)。  
  
## <a name="syntax"></a>語法  
  
```cpp  
private ref class WriteOnlyArray<T, 1>  
```  
  
### <a name="members"></a>成員  
  
### <a name="public-methods"></a>公用方法  
 這些方法的存取範圍都是 internal，也就是說，您只能在 C++ 應用程式或元件內存取這些方法。  
  
|名稱|描述|  
|----------|-----------------|  

|[Writeonlyarray:: Begin](#begin)|指向陣列的第一個元素的迭代器。 |  
|[Writeonlyarray:: Data](#data)|資料緩衝區的指標。 |  
|[Writeonlyarray:: End](#end)|指向陣列中最後一個元素後加一的迭代器。 |  
|[Writeonlyarray:: Fastpass](#fastpass)|表示陣列是否可以使用 FastPass 機制，這是由系統悄悄執行的最佳化。 請勿使用此程式碼中 |  
|[Writeonlyarray:: Length](#length)|傳回陣列中的項目數。 |  
|[Writeonlyarray:: Set](#set)|指定的元素設定為指定的值。 |  

  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `WriteOnlyArray`  
  
### <a name="requirements"></a>需求  
 編譯器選項： **/ZW**  
  
 **中繼資料：** Platform.winmd  
  
 **命名空間：** Platform  

## <a name="begin"></a>  WriteOnlyArray::begin 方法
傳回陣列中第一個元素的指標。  
  
### <a name="syntax"></a>語法  
  
```cpp  
T* begin() const;  
```  
  
### <a name="return-value"></a>傳回值  
 陣列中第一個元素的指標。  
  
### <a name="remarks"></a>備註  
 這個迭代器可與 `std::sort` 這類 STL 演算法搭配使用，針對陣列元素執行作業。  
  


## <a name="data"></a>  WriteOnlyArray::Data 屬性
資料緩衝區的指標。  
  
### <a name="syntax"></a>語法  
  
```cpp  
property T* Data{  
   T* get() const;  
}  
```  
  
### <a name="return-value"></a>傳回值  
 原始陣列位元組的指標。  
  


## <a name="end"></a>  WriteOnlyArray::end 方法
傳回陣列中最後一個元素後加一的指標。  
  
### <a name="syntax"></a>語法  
  
```cpp  
T* end() const;  
```  
  
### <a name="return-value"></a>傳回值  
 陣列中最後一個元素後加一的指標迭代器。  
  
### <a name="remarks"></a>備註  
 這個迭代器可與 STL 演算法搭配使用，針對陣列元素執行像是 `std::sort` 這類作業。  
  


## <a name="fastpass"></a>  WriteOnlyArray::FastPass 屬性
表示是否可以執行內部 FastPass 最佳化。 不適合由使用者程式碼所使用。  
  
### <a name="syntax"></a>語法  
  
```cpp  
property bool FastPass{  
   bool get() const;  
}  
```  
  
### <a name="return-value"></a>傳回值  
 表示陣列是否為 FastPass 的布林值。  
  


## <a name="get"></a>  Writeonlyarray:: Get 方法
傳回位於指定之索引處的元素。  
  
### <a name="syntax"></a>語法  
  
```cpp  
T& get(  
   unsigned int indexArg) const;  
```  
  
### <a name="parameters"></a>參數  
 `indexArg`  
  
### <a name="return-value"></a>傳回值  
  


## <a name="length"></a>  WriteOnlyArray::Length 屬性
傳回呼叫端配置之陣列中元素數目。  
  
### <a name="syntax"></a>語法  
  
```cpp  
property unsigned int Length{  
   unsigned int get() const;  
}  
```  
  
### <a name="return-value"></a>傳回值  
 陣列中的項目數。  
  


## <a name="set"></a>  WriteOnlyArray::set 函式
在陣列中指定的索引處設定指定的值。  
  
### <a name="syntax"></a>語法  
  
```cpp  
T& set(  
   unsigned int indexArg,  
   T valueArg);  
```  
  
### <a name="parameters"></a>參數  
 `indexArg`  
 要設定之元素的索引。  
  
 `valueArg`  
 要在 `indexArg` 設定的值。  
  
### <a name="return-value"></a>傳回值  
 剛才設定之元素的參考。  
  

  
### <a name="remarks"></a>備註  
 如需如何解譯 HRESULT 值的詳細資訊，請參閱[結構 COM 錯誤碼的](http://go.microsoft.com/fwlink/p/?LinkId=262045)。  
  
  
## <a name="see-also"></a>另請參閱  
 [Platform 命名空間](platform-namespace-c-cx.md)   
 [在 c + + 中建立 Windows 執行階段元件](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)