---
title: 使用 __declspec(dllimport) 匯入至應用程式
ms.date: 11/04/2016
helpviewer_keywords:
- __declspec(dllimport) keyword [C++]
- importing DLLs [C++], __declspec(dllimport)
ms.assetid: edb4da4e-f83a-44cf-a668-9239d49dbe42
ms.openlocfilehash: fd7d42ec5a76b92aa789a3a20f38e6b2c0fd2cb1
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440418"
---
# <a name="import-into-an-application-using-__declspecdllimport"></a>使用 __declspec(dllimport) 匯入至應用程式

使用 DLL 所定義之公用符號的程式稱為「匯入」。 當您為使用 Dll 建立的應用程式建立標頭檔時，請在公用符號的宣告上使用 **__declspec （dllimport）** 。 不論您是使用 .def 檔案還是 **__declspec （dllexport）** 關鍵字匯出，關鍵字 **__declspec （dllimport）** 都可以運作。

若要讓您的程式碼更容易閱讀，請定義 **__declspec （dllimport）** 的宏，然後使用宏來宣告每個匯入的符號：

```
#define DllImport   __declspec( dllimport )

DllImport int  j;
DllImport void func();
```

在函式宣告中使用 **__declspec （dllimport）** 是選擇性的，但如果您使用此關鍵字，編譯器會產生更有效率的程式碼。 不過，您必須使用 **__declspec （dllimport）** 來匯入可執行檔，以存取 DLL 的公用資料符號和物件。 請注意，您的 DLL 使用者仍然需要與匯入程式庫連結。

您可以針對 DLL 和用戶端應用程式使用相同的標頭檔。 若要這麼做，請使用特殊的預處理器符號，指出您要建立 DLL 或建立用戶端應用程式。 例如：

```
#ifdef _EXPORTING
   #define CLASS_DECLSPEC    __declspec(dllexport)
#else
   #define CLASS_DECLSPEC    __declspec(dllimport)
#endif

class CLASS_DECLSPEC CExampleA : public CObject
{ ... class definition ... };
```

## <a name="what-do-you-want-to-do"></a>您想要做什麼事？

- [初始化 DLL](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？

- [匯入和匯出內嵌函式](importing-and-exporting-inline-functions.md)

- [相互匯入](mutual-imports.md)

## <a name="see-also"></a>請參閱

[匯入至應用程式](importing-into-an-application.md)
