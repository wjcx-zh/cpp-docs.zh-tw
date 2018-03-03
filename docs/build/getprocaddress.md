---
title: "GetProcAddress |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- GetProcAddress
dev_langs:
- C++
helpviewer_keywords:
- DLLs [C++], GetProcAddress
- ordinal exports [C++]
- GetProcAddress method
ms.assetid: 48d14ae0-47ea-4c5d-96b1-2c158f1a26af
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2bc32c5f6b6ae4ee80c69dff028f05d2b334d920
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="getprocaddress"></a>GetProcAddress
明確連結的 DLL 呼叫的處理序[GetProcAddress](http://msdn.microsoft.com/library/windows/desktop/ms683212)取得 DLL 中匯出函式的位址。 您可以使用傳回的函式指標呼叫 DLL 函式。 **GetProcAddress**接受做為參數的 DLL 模組控制代碼 (由傳回**LoadLibrary**， `AfxLoadLibrary`，或**GetModuleHandle**) 會採用函式的名稱和您要呼叫或函式的匯出序數。  
  
 因為您要呼叫 DLL 函式透過指標而且沒有任何編譯時間類型檢查，請確定函式的參數是正確的如此不逾越在堆疊上配置的記憶體，但造成存取違規。 可協助您提供類型安全的方法之一是查看匯出的函式的函式原型，並建立相符的函式指標的 typedef。 例如:   
  
```  
typedef UINT (CALLBACK* LPFNDLLFUNC1)(DWORD,UINT);  
...  
  
HINSTANCE hDLL;               // Handle to DLL  
LPFNDLLFUNC1 lpfnDllFunc1;    // Function pointer  
DWORD dwParam1;  
UINT  uParam2, uReturnVal;  
  
hDLL = LoadLibrary("MyDLL");  
if (hDLL != NULL)  
{  
   lpfnDllFunc1 = (LPFNDLLFUNC1)GetProcAddress(hDLL,  
                                           "DLLFunc1");  
   if (!lpfnDllFunc1)  
   {  
      // handle the error  
      FreeLibrary(hDLL);  
      return SOME_ERROR_CODE;  
   }  
   else  
   {  
      // call the function  
      uReturnVal = lpfnDllFunc1(dwParam1, uParam2);  
   }  
}  
```  
  
 如何指定您想要呼叫時的函數**GetProcAddress**取決於 DLL 的建置方式。  
  
 如果您所連結的 DLL 以模組定義 (.def) 檔所建立，而且序數的資料列與函式中，您可以只取得匯出序數**匯出**DLL 的.def 檔的區段。 呼叫**GetProcAddress**與匯出序數，而不是函式名稱，會稍微快一點如果 DLL 有許多匯出的函式，因為匯出序數做為索引到 DLL 匯出資料表。 與匯出序數， **GetProcAddress**可以找出直接而不是比較指定的名稱與 DLL 匯出資料表中的函式名稱的函式。 不過，您應該呼叫**GetProcAddress**匯出序數，您可以控制指派序數.def 檔案中匯出的函式時，才使用。  
  
## <a name="what-do-you-want-to-do"></a>請您指定選項。  
  
-   [如何以隱含方式連結到 DLL](../build/linking-an-executable-to-a-dll.md#linking-implicitly)  
  
-   [決定要使用哪一個連結方法](../build/linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)  
  
## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？  
  
-   [LoadLibrary 和 AfxLoadLibrary](../build/loadlibrary-and-afxloadlibrary.md)  
  
-   [FreeLibrary](http://msdn.microsoft.com/library/windows/desktop/ms683152)  
  
-   [使用 DEF 檔從 DLL 匯出](../build/exporting-from-a-dll-using-def-files.md)  
  
## <a name="see-also"></a>請參閱  
 [Visual C++ 中的 DLL](../build/dlls-in-visual-cpp.md)