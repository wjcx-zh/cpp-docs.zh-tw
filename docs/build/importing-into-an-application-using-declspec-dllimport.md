---
title: 使用 __declspec(dllimport) 匯入至應用程式
ms.date: 11/04/2016
helpviewer_keywords:
- __declspec(dllimport) keyword [C++]
- importing DLLs [C++], __declspec(dllimport)
ms.assetid: edb4da4e-f83a-44cf-a668-9239d49dbe42
ms.openlocfilehash: 50b630334cfd8752935b54549190d698fa5136bb
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223976"
---
# <a name="import-into-an-application-using-__declspecdllimport"></a>使用 __declspec(dllimport) 匯入至應用程式

使用 DLL 所定義之公用符號的程式稱為「匯入」。 當您為使用 Dll 來建立的應用程式建立標頭檔時，請 **`__declspec(dllimport)`** 在公用符號的宣告上使用。 **`__declspec(dllimport)`** 不論您是使用 .def 檔案還是關鍵字匯出，關鍵字都可以運作 **`__declspec(dllexport)`** 。

若要讓您的程式碼更容易閱讀，請定義的宏， **`__declspec(dllimport)`** 然後使用宏來宣告每個匯入的符號：

```
#define DllImport   __declspec( dllimport )

DllImport int  j;
DllImport void func();
```

**`__declspec(dllimport)`** 在函式宣告中使用是選擇性的，但如果您使用此關鍵字，編譯器會產生更有效率的程式碼。 不過，您必須使用 **`__declspec(dllimport)`** 來匯入可執行檔，以存取 DLL 的公用資料符號和物件。 請注意，您的 DLL 使用者仍然需要與匯入程式庫連結。

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

- [交互匯入](mutual-imports.md)

## <a name="see-also"></a>另請參閱

[匯入至應用程式](importing-into-an-application.md)
