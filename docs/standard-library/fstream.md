---
title: '&lt;fstream&gt;'
ms.date: 11/04/2016
f1_keywords:
- <fstream>
helpviewer_keywords:
- fstream header
ms.assetid: 660de351-0489-41df-b239-40e0cdcab46b
ms.openlocfilehash: 1f85367b9ae527c9387d085acc1496bfbbf7cc9e
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688030"
---
# <a name="ltfstreamgt"></a>&lt;fstream&gt;

定義可對外部檔案中儲存之序列的 iostreams 作業提供支援的數個類別。

## <a name="syntax"></a>語法

```cpp
#include <fstream>
```

### <a name="typedefs"></a>Typedef

|類型名稱|描述|
|-|-|
|[filebuf](../standard-library/fstream-typedefs.md#filebuf)|類型 `basic_filebuf` 在**char**樣板參數上特製化。|
|[fstream](../standard-library/fstream-typedefs.md#fstream)|類型 `basic_fstream` 在**char**樣板參數上特製化。|
|[ifstream](../standard-library/fstream-typedefs.md#ifstream)|類型 `basic_ifstream` 在**char**樣板參數上特製化。|
|[ofstream](../standard-library/fstream-typedefs.md#ofstream)|類型 `basic_ofstream` 在**char**樣板參數上特製化。|
|[wfstream](../standard-library/fstream-typedefs.md#wfstream)|類型 `basic_fstream` 在**wchar_t**樣板參數上特製化。|
|[wifstream](../standard-library/fstream-typedefs.md#wifstream)|類型 `basic_ifstream` 在**wchar_t**樣板參數上特製化。|
|[wofstream](../standard-library/fstream-typedefs.md#wofstream)|類型 `basic_ofstream` 在**wchar_t**樣板參數上特製化。|
|[wfilebuf](../standard-library/fstream-typedefs.md#wfilebuf)|類型 `basic_filebuf` 在**wchar_t**樣板參數上特製化。|

### <a name="classes"></a>類別

|執行個體|描述|
|-|-|
|[basic_filebuf](../standard-library/basic-filebuf-class.md)|類別樣板描述一個資料流程緩衝區，可控制 `Elem` 類型的專案傳輸，其字元特性是由類別所 `Tr`，以及儲存在外部檔案中的專案序列所決定。|
|[basic_fstream](../standard-library/basic-fstream-class.md)|類別樣板描述的物件可控制如何使用 **> \<** [basic_filebuf](../standard-library/basic-filebuf-class.md)類別的資料流程緩衝區來插入和解壓縮專案和編碼物件，以及`Elem` 類型的元素，其字元特性取決於類別 `Tr`。|
|[basic_ifstream](../standard-library/basic-ifstream-class.md)|類別樣板描述一個物件，它會從 > \< [basic_filebuf](../standard-library/basic-filebuf-class.md)類別**的資料流程緩衝區**中控制專案和編碼物件**的提取**，並將其字元特性設為類型 `Elem` 的元素由類別 `Tr` 決定。|
|[basic_ofstream](../standard-library/basic-ofstream-class.md)|類別樣板描述的物件可控制如何將元素和編碼物件插入 > \< [basic_filebuf](../standard-library/basic-filebuf-class.md)類別的**資料流程緩衝區中**，並以類型 `Elem` 的元素（其字元特性已決定）由類別 `Tr`。|

## <a name="see-also"></a>請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)\
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream 程式設計](../standard-library/iostream-programming.md)\
[iostream 慣例](../standard-library/iostreams-conventions.md)
