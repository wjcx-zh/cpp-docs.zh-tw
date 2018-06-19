---
title: CAdapt 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAdapt
- ATLCOMCLI/ATL::CAdapt
- ATLCOMCLI/ATL::CAdapt::CAdapt
- ATLCOMCLI/ATL::CAdapt::m_T
dev_langs:
- C++
helpviewer_keywords:
- address-of operator
- adapter objects
- '& operator, address-of operator'
- CAdapt class
ms.assetid: 0bb695a5-72fe-43d1-8f39-7e4da6e34765
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cabdf0a396f50f548cbe01a765411120ff7dd9f1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32365594"
---
# <a name="cadapt-class"></a>CAdapt 類別
此範本用來包裝重新定義傳址 (address-of) 運算子的類別，以傳回物件位址以外的內容。  
  
## <a name="syntax"></a>語法  
  
```
template <class T>  
class CAdapt
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 配接的類型。  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CAdapt::CAdapt](#cadapt)|建構函式。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[CAdapt::operator const T （& s)](#operator_const_t_amp)|傳回 `const` 的 `m_T` 參考。|  
|[CAdapt::operator T （& s)](#operator_t_amp)|傳回 `m_T` 的參考。|  
|[CAdapt::operator <](#operator_lt)|將所配接類型的物件與 `m_T` 相比較。|  
|[CAdapt::operator =](#operator_eq)|將所配接類型的物件指派給 `m_T`。|  
|[CAdapt::operator = =](#operator_eq_eq)|將所配接類型的物件與 `m_T` 相比較。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CAdapt::m_T](#m_t)|要配接的資料。|  
  
## <a name="remarks"></a>備註  
 `CAdapt` 是簡單的範本，用來包裝重新定義傳址運算子的類別 ( `operator &`) 來傳回物件位址以外的項目。 這些類別的範例包括 ATL 的 `CComBSTR`、`CComPtr` 和 `CComQIPtr` 類別，以及編譯器 COM 支援類別 `_com_ptr_t`。 這些類別全都會重新定義傳址運算子，以傳回其中一個資料成員的位址 (在 `BSTR` 的情況下是 `CComBSTR`，在其他類別的情況下是介面指標)。  
  
 `CAdapt` 的主要角色是隱藏 `T` 類別所定義的傳址運算子，但是仍然保留所配接類別的特性。 `CAdapt` fulfils 藉由保留的公用成員，這個角色[m_T](#m_t)，型別`T`，並藉由定義轉換運算子、 比較運算子和複製建構函式，以允許的特製化`CAdapt`視為如同它們是類型的物件`T`。  
  
 配接器類別 `CAdapt` 非常實用，因為某些容器樣式類別預期能夠使用傳址運算子取得其內含物件的位址。 因此，重新定義傳址運算子可能會混淆此需求，而這通常會造成編譯錯誤，並且無法使用非配接的類型搭配只要該類型「可運作」的類別。 `CAdapt` 提供了解決這些問題的方式。  
  
 通常，當您要將 `CAdapt`、`CComBSTR`、`CComPtr` 或 `CComQIPtr` 儲存在容器樣式類別中時，會使用 `_com_ptr_t`。 在支援 C++11 標準之前，這對於 C++ 標準程式庫容器而言是最常要執行的工作，不過，C++11 標準程式庫容器會自動搭配具有多載 `operator&()` 的類型運作。 標準程式庫的做法是在內部使用[std::addressof](../../standard-library/memory-functions.md#addressof)取得真正的物件位址。  
  
## <a name="requirements"></a>需求  
 **標頭：** atlcomcli.h  
  
##  <a name="cadapt"></a>  CAdapt::CAdapt  
 建構函式可讓配接器物件建構，複製的物件配接的類型，或從另一個配接器物件複製的預設值。  
  
```
CAdapt();
CAdapt(const T& rSrc);
CAdapt(const CAdapt& rSrCA);
CAdapt(T&& rSrCA);  // (Visual Studio 2017)
CAdapt(CAdapt<T>&& rSrCA) noexcept; // (Visual Studio 2017)
```  
  
### <a name="parameters"></a>參數  
 `rSrc`  
 適用於複製到新建構的配置器物件類型的變數。  
  
 *rSrCA*  
 其包含的資料應該複製 （或移動） 成新建構的配置器物件配接器物件。  
  
##  <a name="m_t"></a>  CAdapt::m_T  
 保留要配接的資料。  
  
```
T m_T;
```  
  
### <a name="remarks"></a>備註  
 這**公用**資料成員可以直接或間接地存取與[運算子 const T &](#operator_const_t_amp)和[T 運算子 （& s)](#operator_t_amp)。  
  
##  <a name="operator_const_t_amp"></a>  CAdapt::operator const T&amp;  
 傳回**const**參考[m_T](#m_t)成員，可讓配接器物件，就好像類型的物件視為`T`。  
  
```  
operator const T&() const;
```  
  
### <a name="return-value"></a>傳回值  
 A **const**參考`m_T`。  
  
##  <a name="operator_t_amp"></a>  CAdapt::operator T&amp;  
 將參考傳回給[m_T](#m_t)成員，可讓配接器物件，就好像類型的物件視為`T`。  
  
```  
operator T&();
```     
  
### <a name="return-value"></a>傳回值  
 若要參考`m_T`。  
  
##  <a name="operator_lt"></a>  CAdapt::operator &lt;  
 比較物件與所配接類型的[m_T](#m_t)。  
  
```
bool operator<(const T& rSrc) const;
```  
  
### <a name="parameters"></a>參數  
 `rSrc`  
 要比較的物件參考。  
  
### <a name="return-value"></a>傳回值  
 之間的比較結果`m_T`和`rSrc`。  
  
##  <a name="operator_eq"></a>  CAdapt::operator =  
 指派運算子指派引數， `rSrc`，資料成員[m_T](#m_t)並傳回目前的配接器物件。  
  
```
CAdapt& operator= (const T& rSrc);
CAdapt& operator= (T&& rSrCA); // (Visual Studio 2017)
CAdapt& operator= (CAdapt<T>&& rSrCA) noexcept; // (Visual Studio 2017)
```  
  
### <a name="parameters"></a>參數  
 `rSrc`  
 要複製所配接類型的物件參考。 

 `rSrCA` 要移動的物件參考。 
  
### <a name="return-value"></a>傳回值  
 目前物件的參考。  
  
##  <a name="operator_eq_eq"></a>  CAdapt::operator = =  
 比較物件與所配接類型的[m_T](#m_t)。  
  
```
bool operator== (const T& rSrc) const;
```  
  
### <a name="parameters"></a>參數  
 `rSrc`  
 要比較的物件參考。  
  
### <a name="return-value"></a>傳回值  
 之間的比較結果`m_T`和`rSrc`。  
  
## <a name="see-also"></a>另請參閱  
 [類別概觀](../../atl/atl-class-overview.md)
