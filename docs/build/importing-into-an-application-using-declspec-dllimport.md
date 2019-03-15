---
title: 將應用程式使用 __declspec （dllimport） 匯入
ms.date: 11/04/2016
f1_keywords:
- __declspec
- dllimport
helpviewer_keywords:
- __declspec(dllimport) keyword [C++]
- importing DLLs [C++], __declspec(dllimport)
ms.assetid: edb4da4e-f83a-44cf-a668-9239d49dbe42
ms.openlocfilehash: 30e0f6517f2d749962c5cf49dddb1662c9ccf129
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57810220"
---
# <a name="import-into-an-application-using-declspecdllimport"></a>將應用程式使用 __declspec （dllimport） 匯入

使用 DLL 所定義的公用符號的程式稱為來匯入它們。 當您建立標頭檔使用您的 Dll，建置應用程式，請使用 **__declspec （dllimport)** 公用符號的宣告。 關鍵字 **__declspec （dllimport)** 不論您匯出.def 檔案，或與運作方式都 **__declspec （dllexport)** 關鍵字。

若要讓您的程式碼更容易閱讀，定義為巨集 **__declspec （dllimport)** ，然後使用巨集宣告每個匯入的符號：

```
#define DllImport   __declspec( dllimport )

DllImport int  j;
DllImport void func();
```

使用 **__declspec （dllimport)** 是選擇性的函式宣告，但如果您使用此關鍵字，編譯器會產生更有效率的程式碼。 不過，您必須使用 **__declspec （dllimport)** 存取 DLL 的公用資料符號和物件匯入可執行檔。 請注意，您的 DLL 的使用者仍然需要與匯入程式庫連結。

您可以使用相同的標頭檔的 DLL] 和 [用戶端應用程式。 若要這樣做，請使用特殊的前置處理器符號，指出是否在建置 DLL，或建置用戶端應用程式。 例如: 

```
#ifdef _EXPORTING
   #define CLASS_DECLSPEC    __declspec(dllexport)
#else
   #define CLASS_DECLSPEC    __declspec(dllimport)
#endif

class CLASS_DECLSPEC CExampleA : public CObject
{ ... class definition ... };
```

## <a name="what-do-you-want-to-do"></a>請您指定選項。

- [初始化 DLL](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？

- [匯入和匯出內嵌函式](importing-and-exporting-inline-functions.md)

- [交互匯入](mutual-imports.md)

## <a name="see-also"></a>另請參閱

[匯入至應用程式](importing-into-an-application.md)
