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

[MFC 擴展 DLL](extension-dlls-overview.md)使用宏**AFX_EXT_CLASS**匯出類;連結到 MFC 擴展 DLL 的可執行檔使用巨集導入類。 使用**AFX_EXT_CLASS**宏時,用於建構 MFC 擴展名 DLL 的相同標頭檔可用於連結到 DLL 的可執行檔。

在 DLL 的標頭檔中,將**AFX_EXT_CLASS**關鍵字添加到類的聲明中,如下所示:

```cpp
class AFX_EXT_CLASS CMyClass : public CDocument
{
// <body of class>
};
```

此宏由 MFC`__declspec(dllexport)`定義為 預`_AFXDLL`處理器`_AFXEXT`符號 和定義時。 但是宏定義為`__declspec(dllimport)``_AFXDLL`何時`_AFXEXT`定義, 並且未定義。 定義時,預處理器符號`_AFXDLL`指示目標可執行檔(DLL 或應用程式)正在使用 MFC 的共用版本。 當和`_AFXDLL``_AFXEXT`都定義時,這表示目標可執行檔是 MFC 擴展 DLL。

由於`AFX_EXT_CLASS`定義為`__declspec(dllexport)`從 MFC 擴展 DLL 匯出時,因此可以匯出整個類,而無需在 .def 檔中放置該類的所有符號的修飾名稱。

儘管可以避免使用此方法創建 .def 檔案和類的所有修飾名稱,但創建 .def 檔案的效率更高,因為名稱可以通過 ddinal 匯出。 要使用 .def 檔案匯出方法,請將以下代碼放在標頭檔的開頭和結尾:

```cpp
#undef AFX_DATA
#define AFX_DATA AFX_EXT_DATA
// <body of your header file>
#undef AFX_DATA
#define AFX_DATA
```

> [!CAUTION]
> 匯出內聯函數時要小心,因為它們可能會造成版本衝突。 內聯函數將擴展到應用程式代碼中;因此,如果以後重寫函數,則不會更新該函數,除非重新編譯應用程式本身。 通常,DLL 函數可以更新,而無需重新生成使用它們的應用程式。

## <a name="exporting-individual-members-in-a-class"></a>匯出類別的單個成員

有時,您可能希望匯出類的各個成員。 例如,如果要匯出`CDialog`派生類,可能只需要匯出構造函數`DoModal`和調用。 您可以在需要匯出`AFX_EXT_CLASS`的單個成員上使用。

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

由於您不再匯出類的所有成員,因此由於 MFC 宏的工作方式,可能會遇到其他問題。 MFC 的幾個幫助宏實際上聲明或定義了數據成員。 因此,這些數據成員也必須從 DLL 匯出。

例如,在構建`DECLARE_DYNAMIC`MFC 擴展 DLL 時,宏的定義如下:

```cpp
#define DECLARE_DYNAMIC(class_name) \
protected: \
   static CRuntimeClass* PASCAL _GetBaseClass(); \
public: \
   static AFX_DATA CRuntimeClass class##class_name; \
   virtual CRuntimeClass* GetRuntimeClass() const; \
```

以靜態`AFX_DATA`開頭的行是在類內部聲明靜態物件。 要正確匯出此類並從用戶端可執行文件訪問運行時資訊,必須匯出此靜態物件。 由於靜態物件是使用修飾`AFX_DATA`符聲明的,因此在構建`AFX_DATA`DLL 時`__declspec(dllexport)`只需定義為 ,並將`__declspec(dllimport)`其定義為構建用戶端 可執行檔時。 因為`AFX_EXT_CLASS`以這種方式定義,你只需要重新`AFX_DATA`定義`AFX_EXT_CLASS`,與 類定義相同。

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

由於 MFC`AFX_DATA`始終在其宏中定義的數據項上使用符號,因此此技術適用於所有此類方案。 例如,它適用於`DECLARE_MESSAGE_MAP`。

> [!NOTE]
> 如果要匯出整個類而不是類的選定成員,則會自動匯出靜態數據成員。

### <a name="what-do-you-want-to-do"></a>您想要做什麼事？

- [使用 .def 檔案從 DLL 匯出](exporting-from-a-dll-using-def-files.md)

- [使用 __declspec(出口)從 DLL 匯出](exporting-from-a-dll-using-declspec-dllexport.md)

- [匯出C++函數,用於 C 語言可執行檔](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [匯出 C 函數,用於 C 或 C++語言可執行檔](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [確定要使用的匯出方法](determining-which-exporting-method-to-use.md)

- [使用 __declspec(dllimport) 匯入至應用程式](importing-into-an-application-using-declspec-dllimport.md)

- [初始化 DLL](run-time-library-behavior.md#initializing-a-dll)

### <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？

- [修飾名稱](reference/decorated-names.md)

- [匯入和匯出內嵌函式](importing-and-exporting-inline-functions.md)

- [相互進口](mutual-imports.md)

## <a name="see-also"></a>另請參閱

[從 DLL 匯出](exporting-from-a-dll.md)
