---
title: GetProcAddress
ms.date: 11/04/2016
f1_keywords:
- GetProcAddress
helpviewer_keywords:
- DLLs [C++], GetProcAddress
- ordinal exports [C++]
- GetProcAddress method
ms.assetid: 48d14ae0-47ea-4c5d-96b1-2c158f1a26af
ms.openlocfilehash: 2d322cfe7d3bd60d8d702a226e181eb7b4ede963
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493256"
---
# <a name="getprocaddress"></a>GetProcAddress

程式會明確連結到 DLL 呼叫[GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress) , 以取得 dll 中匯出函式的位址。 您可以使用傳回的函式指標來呼叫 DLL 函式。 **GetProcAddress**會將 DLL 模組處理 (由**LoadLibrary**、 `AfxLoadLibrary`或**GetModuleHandle**傳回) 做為參數, 並採用您想要呼叫的函式名稱或函數的匯出序數。

因為您是透過指標呼叫 DLL 函式, 而且沒有編譯時間類型檢查, 請確定函式的參數正確無誤, 這樣您才不會 overstep 堆疊上配置的記憶體, 並造成存取違規。 協助提供型別安全的方法之一, 就是查看匯出函式的函數原型, 並為函式指標建立符合的 typedef。 例如：

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

當您呼叫**GetProcAddress**時, 如何指定所需的函式取決於 DLL 的建立方式。

如果您要連結的 DLL 是以模組定義 (.def) 檔案建立的, 而且序數列在 DLL 的 .def 檔案的 [**匯出**] 區段中, 則您只能取得匯出序數。 如果 DLL 有許多匯出的函式, 則呼叫具有匯出序數的**GetProcAddress** (而不是函式名稱) 會稍微快一點, 因為匯出序數會作為 DLL 匯出資料表的索引。 使用匯出序數時, **GetProcAddress**可以直接尋找函式, 而不是將指定的名稱與 DLL 匯出資料表中的函式名稱進行比較。 不過, 只有在您可以控制將序數指派給 .def 檔中匯出的函式時, 才應該使用匯出序數來呼叫**GetProcAddress** 。

## <a name="what-do-you-want-to-do"></a>請您指定選項。

- [將可執行檔連結至 DLL](linking-an-executable-to-a-dll.md#linking-implicitly)

- [將可執行檔連結至 DLL](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)

## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？

- [LoadLibrary 和 AfxLoadLibrary](loadlibrary-and-afxloadlibrary.md)

- [FreeLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-freelibrary)

- [使用 DEF 檔從 DLL 匯出](exporting-from-a-dll-using-def-files.md)

## <a name="see-also"></a>另請參閱

[在 Visual Studio 中建立 C++ DLL](dlls-in-visual-cpp.md)
