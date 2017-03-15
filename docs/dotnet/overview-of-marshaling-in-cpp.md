---
title: "C++ 中封送處理的概觀 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "marshaling"
  - "marshalling"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C++ 支援程式庫, 封送處理"
  - "封送處理, 關於封送處理"
  - "Visual C++, 封送處理"
ms.assetid: 997dd4bc-5f98-408f-b890-f35de9ce3bb8
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C++ 中封送處理的概觀
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在混合模式中，您必須有方式封送處理您在原生及 Managed 資料和 Managed 型別。  [!INCLUDE[vs_orcas_long](../atl/reference/includes/vs_orcas_long_md.md)] 介紹封送處理程式庫以協助您用簡單的方法封送處理和呈現資料。  
  
 您可以使用封送處理程式庫無論有沒有 [marshal\_context 類別](../dotnet/marshal-context-class.md)。  有些轉換需要內容。  使用 [marshal\_as](../dotnet/marshal-as.md) 函式可以實作其他轉換。  下表列出目前支援的轉換，無論它們是否需要內容，以及編譯的檔案必須包含:  
  
|來自型別:|到型別|封送處理方法|包含檔案|  
|-----------|---------|------------|----------|  
|System::String^|const char \*|marshal\_context|marshal.h|  
|const char \*|System::String^|marshal\_as|marshal.h|  
|char\*|System::String^|marshal\_as|marshal.h|  
|System::String^|const wchar\_t\*|marshal\_context|marshal.h|  
|const wchar\_t \*|System::String^|marshal\_as|marshal.h|  
|wchar\_t\*|System::String^|marshal\_as|marshal.h|  
|System::IntPtr。|HANDLE|marshal\_as|marshal\_windows.h|  
|HANDLE|System::IntPtr。|marshal\_as|marshal\_windows.h|  
|System::String^|BSTR|marshal\_context|marshal\_windows.h|  
|BSTR|System::String^|marshal\_as|marshal.h|  
|System::String^|bstr\_t|marshal\_as|marshal\_windows.h|  
|bstr\_t|System::String^|marshal\_as|marshal\_windows.h|  
|System::String^|std::string|marshal\_as|marshal\_cppstd.h|  
|std::string|System::String^|marshal\_as|marshal\_cppstd.h|  
|System::String^|std::wstring|marshal\_as|marshal\_cppstd.h|  
|std::wstring|System::String^|marshal\_as|marshal\_cppstd.h|  
|System::String^|CStringT\<char\>|marshal\_as|marshal\_atl.h|  
|CStringT\<char\>|System::String^|marshal\_as|marshal\_atl.h|  
|System::String^|CStringT\<wchar\_t\>|marshal\_as|marshal\_atl.h|  
|CStringT\<wchar\_t\>|System::String^|marshal\_as|marshal\_atl.h|  
|System::String^|CComBSTR|marshal\_as|marshal\_atl.h|  
|CComBSTR|System::String^|marshal\_as|marshal\_atl.h|  
  
 只有在您從 Managed 封送處理為原生資料型別，您要轉換的原生型別沒有自動的解構函式清除時，封送處理才需要內容，。  封送處理內容在其解構函式中終結配置的原生資料型別。  因此，只有在內容刪除後需要內容的轉換才有效，。  若要儲存所有封送處理的值，您必須將值複製到您的變數。  
  
> [!NOTE]
>  如果您在字串中嵌入 `NULL`，則無法保證封送處理字串的結果。  內嵌 `NULL`可能導致資料截斷或它們可能儲存。  
  
 封送處理程式庫集合中位於指定 msclr 子目錄的 Include 目錄。  這個範例會顯示如何將 msclr 目錄從 include的標頭宣告:  
  
 `#include "msclr\marshal_cppstd.h"`  
  
 封送處理程式庫是可擴充的，以便將封送處理型別。  如需封送處理程式庫的詳細資訊，請參閱 [如何：擴充封送處理程式庫](../dotnet/how-to-extend-the-marshaling-library.md)。  
  
 在較舊的版本中，您可以使用 [平台叫用](../Topic/Consuming%20Unmanaged%20DLL%20Functions.md) 以封送處理資料。  如需 `PInvoke` 的詳細資訊，請參閱 [從 Managed 程式碼呼叫原生函式](../dotnet/calling-native-functions-from-managed-code.md)。  
  
## 請參閱  
 [C\+\+ 支援程式庫](../dotnet/cpp-support-library.md)   
 [如何：擴充封送處理程式庫](../dotnet/how-to-extend-the-marshaling-library.md)