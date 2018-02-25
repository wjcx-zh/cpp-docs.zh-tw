---
title: '&lt;fstream&gt; | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- <fstream>
dev_langs:
- C++
helpviewer_keywords:
- fstream header
ms.assetid: 660de351-0489-41df-b239-40e0cdcab46b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e479caecbca33a19854f6800a037eb093d0b2f5a
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="ltfstreamgt"></a>&lt;fstream&gt;
定義可對外部檔案中儲存之序列的 iostreams 作業提供支援的數個類別。  
  
## <a name="syntax"></a>語法  
  
```  
#include <fstream>  
  
```  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[filebuf](../standard-library/fstream-typedefs.md#filebuf)|`char` 範本參數上的特殊類型 `basic_filebuf`。|  
|[fstream](../standard-library/fstream-typedefs.md#fstream)|`char` 範本參數上的特殊類型 `basic_fstream`。|  
|[ifstream](../standard-library/fstream-typedefs.md#ifstream)|`char` 範本參數上的特殊類型 `basic_ifstream`。|  
|[ofstream](../standard-library/fstream-typedefs.md#ofstream)|`char` 範本參數上的特殊類型 `basic_ofstream`。|  
|[wfstream](../standard-library/fstream-typedefs.md#wfstream)|`wchar_t` 範本參數上的特殊類型 `basic_fstream`。|  
|[wifstream](../standard-library/fstream-typedefs.md#wifstream)|`wchar_t` 範本參數上的特殊類型 `basic_ifstream`。|  
|[wofstream](../standard-library/fstream-typedefs.md#wofstream)|`wchar_t` 範本參數上的特殊類型 `basic_ofstream`。|  
|[wfilebuf](../standard-library/fstream-typedefs.md#wfilebuf)|`wchar_t` 範本參數上的特殊類型 `basic_filebuf`。|  
  
### <a name="classes"></a>類別  
  
|||  
|-|-|  
|[basic_filebuf](../standard-library/basic-filebuf-class.md)|此範本類別描述的資料流緩衝區，可控制 **Elem** 類型的元素 (其字元特性由類別 **Tr** 所決定) 與外部檔案中儲存之元素序列間的往來傳輸。|  
|[basic_fstream](../standard-library/basic-fstream-class.md)|此範本類別描述一個物件，該物件可以搭配使用 [basic_filebuf](../standard-library/basic-filebuf-class.md)\<**Elem**, **Tr**> 類別的資料流緩衝區與 **Elem** 類型的元素 (其字元特性由 **Tr** 類別所決定)，來控制元素和編碼物件的插入及擷取作業。|  
|[basic_ifstream](../standard-library/basic-ifstream-class.md)|此範本類別描述一個物件，該物件可以使用 **Elem** 類型的元素 (其字元特性由 **Tr** 類別所決定)，控制來自 [basic_filebuf](../standard-library/basic-filebuf-class.md)\<**Elem**, **Tr**> 類別的資料流緩衝區之元素和編碼物件的擷取作業。|  
|[basic_ofstream](../standard-library/basic-ofstream-class.md)|此範本類別描述一個物件，該物件可以使用 **Elem** 類型的元素 (其字元特性由 **Tr** 類別所決定)，控制將元素和編碼物件插入 [basic_filebuf](../standard-library/basic-filebuf-class.md)\<**Elem**, **Tr**> 類別的資料流緩衝區。|  
  
## <a name="see-also"></a>請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)   
 [C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream 程式設計](../standard-library/iostream-programming.md)   
 [iostream 慣例](../standard-library/iostreams-conventions.md)



