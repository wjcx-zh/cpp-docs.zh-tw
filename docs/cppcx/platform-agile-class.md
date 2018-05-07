---
title: 'Platform:: agile 類別 |Microsoft 文件'
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- AGILE/Platform::Platform
- AGILE/Platform::Platform::Agile::Agile
- AGILE/Platform::Platform::Agile::Get
- AGILE/Platform::Platform::Agile::GetAddressOf
- AGILE/Platform::Platform::Agile::GetAddressOfForInOut
- AGILE/Platform::Platform::Agile::Release
dev_langs:
- C++
helpviewer_keywords:
- Platform::Agile
ms.assetid: e34459a9-c429-4c79-97fd-030c43ca4155
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4d7d2299dd1395e93f4cd88cbeaec6c0b9467308
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="platformagile-class"></a>Platform::Agile 類別
以 Agile 物件來表示具有 MashalingBehavior=Standard 的物件，可大幅降低發生執行階段執行緒例外狀況的機會。 `Agile<T>` 可讓非 Agile 物件呼叫相同或不同的執行緒，或者從中被呼叫。 如需詳細資訊，請參閱[執行緒和封送處理](../cppcx/threading-and-marshaling-c-cx.md)。  
  
## <a name="syntax"></a>語法  
  
```cpp  
template <typename T>  
class Agile;  
```  
  
#### <a name="parameters"></a>參數  
 T  
 非 Agile 類別的 typename。  
  
### <a name="remarks"></a>備註  
 大部分的 Windows 執行階段中的類別為敏捷式。 Agile 物件可以在相同或不同的執行緒中呼叫同處理序或跨處理序物件，或者從中被呼叫。 如果物件不是 Agile，請將非 Agile 物件包裝在 Agile 的 `Agile<T>` 物件中。 這樣就可以封送處理 `Agile<T>` 物件，且可以使用基礎的非 Agile 物件。  
  
 `Agile<T>` 類別是原生、標準 C++ 類別，需要 `agile.h`。 它代表非 Agile 物件和 Agile 物件的 *「內容」*(context)。 內容指定 Agile 物件的執行緒模型和封送處理行為。 作業系統使用內容來決定如何將物件封送處理。  
  
### <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[Agile::Agile](#ctor)|初始化 Agile 類別的新執行個體。|  
|[Agile::~Agile 解構函式](#dtor)|終結 Agile 類別的目前執行個體。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[Agile::Get](#get)|傳回目前 Agile 物件所代表的物件控制代碼。|  
|[Agile::GetAddressOf](#getaddressof)|重新初始化目前 Agile 物件，然後傳回 `T`類型物件的控制代碼位址。|  
|[Agile::GetAddressOfForInOut](#getaddressofforinout)|傳回目前 Agile 物件所代表的物件的控制代碼位址。|  
|[Agile::Release](#release)|捨棄目前 Agile 物件的基礎物件和內容。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[Agile::operator->](#operator-arrow)|擷取目前 Agile 物件所代表的物件控制代碼。|  
|[Agile::operator=](#operator-assign)|將指定的值指派給目前 Agile 物件。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `Object`  
  
 `Agile`  
  
### <a name="requirements"></a>需求  
 **最低支援用戶端：** Windows 8  
  
 **最低支援伺服器：** Windows Server 2012  
  
 **命名空間：** Platform  
  
 **標頭：** agile.h  

## <a name="ctor"></a>  Agile:: agile 建構函式
初始化 Agile 類別的新執行個體。  
  
## <a name="syntax"></a>語法  
  
```cpp  
  
 Agile();  
  
Agile(T^ object);   
  
Agile(const Agile<T>& object);  
  
Agile(Agile<T>&& object);  
  
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 樣板 typename 參數指定的類型。  
  
 `object`  
 在此建構函式的第二個版本中，是用來初始化新 Agile 執行個體的物件。 在第三個版本中，是複製到新 Agile 執行個體的物件。 在第四個版本中，是移動到新 Agile 執行個體的物件。  
  
### <a name="remarks"></a>備註  
 此建構函式的第一個版本是預設建構函式。 第二個版本從 `object` 參數指定之物件，初始化新的 Agile 執行個體類別。 第三個版本是複製建構函式。 第四個版本是移動建構函式。 這個建構函式不會擲回例外狀況。  

## <a name="dtor"></a>  Agile:: ~ Agile 解構函式
終結 Agile 類別的目前執行個體。  
  
## <a name="syntax"></a>語法  
  
```cpp  
  
~Agile();  
```  
  
### <a name="remarks"></a>備註  
 此解構函式也會釋放目前 Agile 物件表示的物件。  
  
## <a name="get"></a>   Agile:: get 方法
傳回目前 Agile 物件所代表的物件控制代碼。  
  
## <a name="syntax"></a>語法  
  
```cpp  
  
   T^ Get() const  
;  
```  
  
### <a name="return-value"></a>傳回值  
 目前 Agile 物件所代表的物件控制代碼。  
  
 傳回值的類型實際上是不公開的內部類型。 便利的方式來保留傳回值，將它指派給所宣告變數**自動**型别推斷關鍵字。 例如，`auto x = myAgileTvariable->Get();`。  
  
## <a name="getaddressof"></a>  Agile:: getaddressof 方法
重新初始化目前 Agile 物件，然後傳回 `T`類型物件的控制代碼位址。  
  
## <a name="syntax"></a>語法  
  
```cpp  
  
T^* GetAddressOf()   
throw();  
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 樣板 typename 參數指定的類型。  
  
### <a name="return-value"></a>傳回值  
 類型的物件控制代碼位址`T`。  
  
### <a name="remarks"></a>備註  
 這個作業釋放目前的類型的物件表示`T`，如果有則重新初始化 Agile 物件的資料成員，則取得目前執行緒的內容;，然後傳回可以代表物件的控制代碼變數的位址非 agile 物件。 若要讓 Agile 類別執行個體來代表的物件，使用指派運算子 ([agile:: operator =](#operator-assign)) 將物件指派給 Agile 類別執行個體。  

## <a name="getaddressofforinout"></a>  Agile:: getaddressofforinout 方法
傳回目前 Agile 物件所代表的物件的控制代碼位址。  
  
## <a name="syntax"></a>語法  
  
```cpp  
  
T^* GetAddressOfForInOut()  throw();  
  
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 樣板 typename 參數指定的類型。  
  
### <a name="return-value"></a>傳回值  
 目前 Agile 物件所代表的物件的控制代碼位址。  
  
### <a name="remarks"></a>備註  
 這個作業取得目前執行緒的內容，然後傳回基礎物件的控制代碼位址。  

## <a name="release"></a>  Agile:: release 方法
捨棄目前 Agile 物件的基礎物件和內容。  
  
## <a name="syntax"></a>語法  
  
```cpp  
  
void Release() throw();  
  
```  
  
### <a name="remarks"></a>備註  
 捨棄目前 Agile 物件的基礎物件和內容 (如果存在的話)，然後將 Agile 物件的值設為 null。  

## <a name="operator-arrow"></a>  Agile:: operator-&gt;運算子
擷取目前 Agile 物件所代表的物件控制代碼。  
  
## <a name="syntax"></a>語法  
  
```cpp  
  
T^ operator->()   
const throw();  
```  
  
### <a name="return-value"></a>傳回值  
 目前 Agile 物件所代表的物件控制代碼。  
  
 這個運算子實際傳回保密的內部類型。 便利的方式來保留傳回值，將它指派給所宣告變數**自動**型别推斷關鍵字。  

## <a name="operator-assign"></a>  Agile:: operator = 運算子
將指定的物件指派給目前 Agile 物件。  
  
## <a name="syntax"></a>語法  
  
```cpp  
  
   Agile<T> operator=(T^ object) throw();  
  
   Agile<T> operator=(  
      const Agile<T>& object  
) throw();  
  
   Agile<T> operator=(  
      Agile<T>&& object  
) throw();  
  
   T^ operator=(  
      IUnknown* lp  
) throw();  
  
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 typename 樣板指定的類型。  
  
 `object`  
 複製或移至目前 Agile 物件的物件或物件控制代碼。  
  
 `lp`  
 物件的 IUnknown 介面指標。  
  
### <a name="return-value"></a>傳回值  
 `T` 類型物件的控制代碼  
  
### <a name="remarks"></a>備註  
 指派運算子的第一個版本會將參考類型的控制代碼複製到目前 Agile 物件。 第二個版本複製 Agile 類型的參考至目前 Agile 物件。 第三個版本移動 Agile 類型至目前 Agile 物件。 第四個版本移動 COM 物件的指標至目前 Agile 物件。  
  
 指派作業會自動保存目前 Agile 物件的內容。 
       
## <a name="see-also"></a>另請參閱  
 [Platform 命名空間](platform-namespace-c-cx.md)