---
title: 使用 AFX_EXT_CLASS 匯出和匯入
ms.date: 11/04/2016
f1_keywords:
- afx_ext_class
helpviewer_keywords:
- AFX_EXT_CLASS macro
- exporting classes [C++]
- importing DLLs [C++]
- extension DLLs [C++], exporting classes
- executable files [C++], importing classes
- exporting DLLs [C++], AFX_EXT_CLASS macro
ms.assetid: 6b72cb2b-e92e-4ecd-bcab-c335e1d1cfde
ms.openlocfilehash: 95c72f8251a8a59833483eb948709c80a69d03d7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328602"
---
# <a name="exporting-and-importing-using-afx_ext_class"></a>使用 AFX_EXT_CLASS 匯出和匯入

[MFC 擴充 dll](extension-dlls-overview.md)使用宏**AFX_EXT_CLASS**來匯出類別;連結至 MFC 延伸模組 DLL 的可執行檔會使用宏來匯入類別。 使用**AFX_EXT_CLASS**宏，用來建立 MFC 延伸模組 DLL 的相同標頭檔，可以與連結至 DLL 的可執行檔搭配使用。

在您 DLL 的標頭檔中，將**AFX_EXT_CLASS**關鍵字新增至類別的宣告，如下所示：

```cpp
class AFX_EXT_CLASS CMyClass : public CDocument
{
// <body of class>
};
```

這個宏是由 MFC 定義， `__declspec(dllexport)`如同預處理器符號`_AFXDLL`和`_AFXEXT`定義時一樣。 但巨集定義的定義是`__declspec(dllimport)`在定義`_AFXDLL`時，且`_AFXEXT`未定義。 當定義時，預處理器`_AFXDLL`符號會指出目標可執行檔（DLL 或應用程式）正在使用 MFC 的共用版本。 當`_AFXDLL`和`_AFXEXT`都已定義時，這表示目標可執行檔是 MFC 延伸 DLL。

因為`AFX_EXT_CLASS`在從 MFC `__declspec(dllexport)`延伸模組 DLL 匯出時定義為，所以您可以匯出整個類別，而不需要將該類別的所有符號裝飾名稱放在 .def 檔案中。

雖然您可以避免使用這個方法來建立 .def 檔案和類別的所有裝飾名稱，但是建立 .def 檔案會更有效率，因為序數可以匯出名稱。 若要使用匯出的 .def 檔案方法，請將下列程式碼放在標頭檔的開頭和結尾處：

```cpp
#undef AFX_DATA
#define AFX_DATA AFX_EXT_DATA
// <body of your header file>
#undef AFX_DATA
#define AFX_DATA
```

> [!CAUTION]
> 匯出內嵌函式時請務必小心，因為它們可能會產生版本衝突的可能性。 內嵌函式會展開為應用程式代碼;因此，如果您稍後重寫函式，除非重新編譯應用程式本身，否則不會更新該函式。 一般來說，可以更新 DLL 函式，而不需要重建使用它們的應用程式。

## <a name="exporting-individual-members-in-a-class"></a>匯出類別中的個別成員

有時候，您可能會想要匯出類別的個別成員。 例如，如果您要匯出`CDialog`衍生的類別，您可能只需要匯出該函數和`DoModal`呼叫。 您可以在`AFX_EXT_CLASS`需要匯出的個別成員上使用。

例如：

```cpp
class CExampleDialog : public CDialog
{
public:
   AFX_EXT_CLASS CExampleDialog();
   AFX_EXT_CLASS int DoModal();
   ...
   // rest of class definition
   ...
};
```

因為您不再匯出類別的所有成員，所以可能會因為 MFC 宏的運作方式而遇到額外的問題。 MFC 的幾個 helper 宏實際上會宣告或定義資料成員。 因此，這些資料成員也必須從您的 DLL 匯出。

例如，建立 MFC `DECLARE_DYNAMIC`延伸 DLL 時，宏的定義如下：

```cpp
#define DECLARE_DYNAMIC(class_name) \
protected: \
   static CRuntimeClass* PASCAL _GetBaseClass(); \
public: \
   static AFX_DATA CRuntimeClass class##class_name; \
   virtual CRuntimeClass* GetRuntimeClass() const; \
```

以 static `AFX_DATA`開頭的那一行會在您的類別內宣告靜態物件。 若要正確匯出此類別，並從用戶端可執行檔存取執行時間資訊，您必須匯出這個靜態物件。 因為靜態`AFX_DATA`物件是使用修飾詞所宣告，所以您只需要在`AFX_DATA`建立 DLL `__declspec(dllexport)`時定義為，並在建立客戶`__declspec(dllimport)`端可執行檔時將它定義為。 由於`AFX_EXT_CLASS`已經以這種方式定義，因此您只需要重新`AFX_DATA`定義，就可以與`AFX_EXT_CLASS`您的類別定義大致相同。

例如：

```cpp
#undef  AFX_DATA
#define AFX_DATA AFX_EXT_CLASS

class CExampleView : public CView
{
   DECLARE_DYNAMIC()
   // ... class definition ...
};

#undef  AFX_DATA
#define AFX_DATA
```

因為 MFC 一律會在`AFX_DATA`其宏內定義的資料項目上使用符號，所以這項技術適用于所有這類情況。 例如，它適用于`DECLARE_MESSAGE_MAP`。

> [!NOTE]
> 如果您要匯出整個類別，而不是類別的選取成員，則會自動匯出靜態資料成員。

### <a name="what-do-you-want-to-do"></a>您想要做什麼事？

- [使用 .def 檔從 DLL 匯出](exporting-from-a-dll-using-def-files.md)

- [使用 __declspec （dllexport）從 DLL 匯出](exporting-from-a-dll-using-declspec-dllexport.md)

- [匯出 c + + 函式以用於 C 語言可執行檔](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [匯出 C 函式以用於 C 或 c + + 語言可執行檔](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [判斷要使用哪一個匯出方法](determining-which-exporting-method-to-use.md)

- [使用 __declspec(dllimport) 匯入至應用程式](importing-into-an-application-using-declspec-dllimport.md)

- [初始化 DLL](run-time-library-behavior.md#initializing-a-dll)

### <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？

- [裝飾名稱](reference/decorated-names.md)

- [匯入和匯出內嵌函式](importing-and-exporting-inline-functions.md)

- [相互匯入](mutual-imports.md)

## <a name="see-also"></a>請參閱

[從 DLL 匯出](exporting-from-a-dll.md)
