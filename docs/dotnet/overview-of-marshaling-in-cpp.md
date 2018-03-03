---
title: "C + + 中封送處理的概觀 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- marshaling
- marshalling
dev_langs:
- C++
helpviewer_keywords:
- Visual C++, marshaling
- C++ Support Library, marshaling
- marshaling, about marshaling
ms.assetid: 997dd4bc-5f98-408f-b890-f35de9ce3bb8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 9d910c7d6346d23f094e9359f0e5fe3536ee09dc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="overview-of-marshaling-in-c"></a>C++ 中封送處理的概觀
在混合模式中，您有時必須封送處理您原生與 managed 型別之間的資料。 [!INCLUDE[vs_orcas_long](../atl/reference/includes/vs_orcas_long_md.md)]導入了封送處理程式庫，可協助您封送處理，並將資料轉換的簡單方式。  
  
 您可以使用封送處理，不論[marshal_context 類別](../dotnet/marshal-context-class.md)。 某些轉換需要的內容。 其他轉換可使用實作[marshal_as](../dotnet/marshal-as.md)函式。 下表列出支援的目前轉換、 是否需要內容，並封送處理的檔案必須包含：  
  
|從型別|若要輸入|封送處理方法|Include 檔|  
|---------------|-------------|--------------------|------------------|  
|System:: string ^|const char *|marshal_context|marshal.h|  
|const char *|System:: string ^|marshal_as|marshal.h|  
|char *|System:: string ^|marshal_as|marshal.h|  
|System:: string ^|const wchar_t*|marshal_context|marshal.h|  
|const wchar_t *|System:: string ^|marshal_as|marshal.h|  
|wchar_t *|System:: string ^|marshal_as|marshal.h|  
|System::IntPtr|HANDLE|marshal_as|marshal_windows.h|  
|HANDLE|System::IntPtr|marshal_as|marshal_windows.h|  
|System:: string ^|BSTR|marshal_context|marshal_windows.h|  
|BSTR|System:: string ^|marshal_as|marshal.h|  
|System:: string ^|bstr_t|marshal_as|marshal_windows.h|  
|bstr_t|System:: string ^|marshal_as|marshal_windows.h|  
|System:: string ^|std:: string|marshal_as|marshal_cppstd.h|  
|std:: string|System:: string ^|marshal_as|marshal_cppstd.h|  
|System:: string ^|std:: wstring|marshal_as|marshal_cppstd.h|  
|std:: wstring|System:: string ^|marshal_as|marshal_cppstd.h|  
|System:: string ^|CStringT\<char >|marshal_as|marshal_atl.h|  
|CStringT\<char >|System:: string ^|marshal_as|marshal_atl.h|  
|System:: string ^|CStringT < wchar_t >|marshal_as|marshal_atl.h|  
|CStringT < wchar_t >|System:: string ^|marshal_as|marshal_atl.h|  
|System:: string ^|CComBSTR|marshal_as|marshal_atl.h|  
|CComBSTR|System:: string ^|marshal_as|marshal_atl.h|  
  
 封送處理需要的內容，只有在您封送處理為原生受管理的資料類型，而您要將它轉換成原生型別並沒有解構函式自動清除。 封送處理的內容會終結其解構函式中的已配置的原生資料類型。 因此，需要內容的轉換將會是有效的內容會被刪除後，才。 若要儲存任何封送處理的值，您必須將值複製到您自己的變數。  
  
> [!NOTE]
>  如果您已嵌入`NULL`s 在字串中的，不保證封送處理字串的結果。 內嵌`NULL`可能會導致要截斷的字串，或可能會保留。  
  
 封送處理程式庫標頭位於 msclr 子目錄中的包含目錄中。 這個範例示範如何在包含標頭宣告包含 msclr 目錄：  
  
 `#include "msclr\marshal_cppstd.h"`  
  
 封送處理程式庫是可延伸，好讓您可以加入您自己的封送處理類型。 如需擴充封送處理程式庫的詳細資訊，請參閱[如何： 擴充封送處理程式庫](../dotnet/how-to-extend-the-marshaling-library.md)。  
  
 在舊版中，您無法封送處理資料使用[平台叫用](/dotnet/framework/interop/consuming-unmanaged-dll-functions)。 如需有關`PInvoke`，請參閱[從 Managed 程式碼呼叫原生函式](../dotnet/calling-native-functions-from-managed-code.md)。  
  
## <a name="see-also"></a>請參閱  
 [C + + 支援程式庫](../dotnet/cpp-support-library.md)   
 [如何：擴充封送處理程式庫](../dotnet/how-to-extend-the-marshaling-library.md)