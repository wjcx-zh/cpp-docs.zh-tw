---
title: "匯出和匯入使用 AFX_EXT_CLASS |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: afx_ext_class
dev_langs: C++
helpviewer_keywords:
- AFX_EXT_CLASS macro
- exporting classes [C++]
- importing DLLs [C++]
- extension DLLs [C++], exporting classes
- executable files [C++], importing classes
- exporting DLLs [C++], AFX_EXT_CLASS macro
ms.assetid: 6b72cb2b-e92e-4ecd-bcab-c335e1d1cfde
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: fb47703b7cd4ef2d0493016c120db0b7d845a71f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="exporting-and-importing-using-afxextclass"></a>使用 AFX_EXT_CLASS 匯出和匯入  
  
[MFC 擴充 Dll](../build/extension-dlls-overview.md)使用巨集**AFX_EXT_CLASS**表示匯出的類別，則連結至 MFC 擴充 DLL 的可執行檔匯入類別使用巨集。 與**AFX_EXT_CLASS**巨集，可用來建置 MFC 擴充功能 DLL 可以搭配連結至 DLL 的可執行檔的相同標頭檔。  
  
 在您的 DLL 的標頭檔，加入**AFX_EXT_CLASS**關鍵字加入類別的宣告，如下所示：  
  
```cpp  
class AFX_EXT_CLASS CMyClass : public CDocument  
{  
// <body of class>  
};  
```  
  
由 MFC 做為定義此巨集`__declspec(dllexport)`時的前置處理器符號`_AFXDLL`和`_AFXEXT`所定義。 但巨集會定義為`__declspec(dllimport)`時`_AFXDLL`定義和`_AFXEXT`未定義。 定義時，前置處理器符號`_AFXDLL`指出共用的 MFC 版本由目標可執行檔 （DLL 或應用程式）。 當同時`_AFXDLL`和`_AFXEXT`所定義，這表示目標可執行檔的 MFC 擴充 DLL。  
  
因為`AFX_EXT_CLASS`定義為`__declspec(dllexport)`時從 MFC 擴充 DLL 的匯出，您可以匯出整個類別，而不將所有該類別的符號的裝飾的名稱放入.def 檔。  
  
雖然您可以避免使用這個方法來建立.def 檔和所有裝飾名稱的類別，建立.def 檔會更有效率因為可以依序數匯出名稱。 若要使用.def 檔的匯出的方法，將下列程式碼放置在開頭和結尾的標頭檔：  
  
```cpp  
#undef AFX_DATA  
#define AFX_DATA AFX_EXT_DATA  
// <body of your header file>  
#undef AFX_DATA  
#define AFX_DATA  
```  
  
> [!CAUTION]
>  時請小心匯出內嵌函式，因為它們可能會產生版本衝突。 內嵌函式展開成應用程式程式碼中。因此，如果您稍後重新撰寫函式，它就不會更新除非重新編譯應用程式本身。 一般來說，可以更新 DLL 函式，而不需重建使用它們的應用程式。  
  
## <a name="exporting-individual-members-in-a-class"></a>匯出類別中的個別成員  
  
有時候您可能想要匯出您的類別中的個別成員。 例如，如果您要匯出`CDialog`-衍生的類別，您可能只需要將匯出的建構函式和`DoModal`呼叫。 您可以使用`AFX_EXT_CLASS`上您要匯出的個別成員。  
  
例如:   
  
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
  
因為您不會再匯出類別的所有成員，則可能會發生其他問題方式 MFC 巨集可。 有幾個 MFC 的協助程式巨集實際宣告或定義的資料成員。 因此，這些資料成員也必須從您的 DLL 匯出。  
  
例如，`DECLARE_DYNAMIC`建置 MFC 擴充 DLL 時，如下所示定義巨集：  
  
```cpp  
#define DECLARE_DYNAMIC(class_name) \  
protected: \  
   static CRuntimeClass* PASCAL _GetBaseClass(); \  
public: \  
   static AFX_DATA CRuntimeClass class##class_name; \  
   virtual CRuntimeClass* GetRuntimeClass() const; \  
```  
  
靜態的開頭行`AFX_DATA`會宣告您的類別內的靜態物件。 若要正確地匯出這個類別，並從可執行的用戶端存取執行階段資訊，您必須匯出此靜態物件。 因為以修飾詞宣告靜態物件`AFX_DATA`，您只需要定義`AFX_DATA`是`__declspec(dllexport)`建置 DLL 時，它定義為`__declspec(dllimport)`建置您的用戶端可執行檔時。 因為`AFX_EXT_CLASS`已經定義過了這種方式，您只需要重新定義`AFX_DATA`是相同`AFX_EXT_CLASS`周圍類別定義。  
  
例如:   
  
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
  
因為一律會使用 MFC`AFX_DATA`所有這類案例中此技術適用於在其巨集，它定義的資料項目上符號。 比方說，這也適用於`DECLARE_MESSAGE_MAP`。  
  
> [!NOTE]
>  如果您要匯出整個類別，而不是所選的類別的成員，靜態資料成員會自動匯出。  
  
### <a name="what-do-you-want-to-do"></a>請您指定選項。  
  
-   [使用.def 檔從 DLL 匯出](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [使用 __declspec （dllexport） 從 DLL 匯出](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
-   [匯出 c + + 函式，以用於 C 語言可執行檔](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)  
  
-   [匯出 C 函式，以用於 C 或 c + + 語言可執行檔](../build/exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)  
  
-   [決定要使用哪一個匯出方法](../build/determining-which-exporting-method-to-use.md)  
  
-   [匯入應用程式使用 __declspec （dllimport）](../build/importing-into-an-application-using-declspec-dllimport.md)  
  
-   [初始化 DLL](../build/run-time-library-behavior.md#initializing-a-dll)  
  
### <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？  
  
-   [裝飾的名稱](../build/reference/decorated-names.md)  
  
-   [匯入和匯出內嵌函式](../build/importing-and-exporting-inline-functions.md)  
  
-   [交互匯入](../build/mutual-imports.md)  
  
## <a name="see-also"></a>請參閱  
 [從 DLL 匯出](../build/exporting-from-a-dll.md)