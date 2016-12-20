---
title: "使用 AFX_EXT_CLASS 匯出和匯入 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "afx_ext_class"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AFX_EXT_CLASS 巨集"
  - "可執行檔 [C++], 匯入類別"
  - "匯出類別 [C++]"
  - "匯出 DLL [C++], AFX_EXT_CLASS 巨集"
  - "擴充 DLL [C++], 匯出類別"
  - "匯入 DLL [C++]"
ms.assetid: 6b72cb2b-e92e-4ecd-bcab-c335e1d1cfde
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 使用 AFX_EXT_CLASS 匯出和匯入
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[擴充 DLL](../build/extension-dlls-overview.md) 會使用 **AFX\_EXT\_CLASS** 巨集來匯出類別；連結至擴充 DLL 的可執行檔則會使用巨集來匯入類別。  使用 **AFX\_EXT\_CLASS** 巨集，用來建置擴充 DLL 的相同標頭檔便可以用在連結至該 DLL 的可執行檔。  
  
 在您的 DLL 的標頭檔中，依照下列方式將 **AFX\_EXT\_CLASS** 關鍵字加入至類別宣告中：  
  
```  
class AFX_EXT_CLASS CMyClass : public CDocument  
{  
// <body of class>  
};  
```  
  
 這個巨集會在前置處理器符號 **\_AFXDLL** 和 `_AFXEXT` 已定義時，由 MFC 定義成 **\_\_declspec\(dllexport\)**。  但是會在已定義 **\_AFXDLL** 卻沒有定義 `_AFXEXT` 時，定義成 **\_\_declspec\(dllimport\)**。  當已定義時，前置處理器符號 **\_AFXDLL** 便會指示出目標可執行檔 \(DLL 或應用程式\) 已經使用 MFC 的共用版本。  當 **\_AFXDLL** 和 `_AFXEXT` 都已定義時，該巨集便會指示，該目標可執行檔是一個擴充 DLL。  
  
 因為從擴充 DLL 匯出時 **AFX\_EXT\_CLASS** 是定義成 **\_\_declspec\(dllexport\)**，所以您不需要在 .def 檔中為該類別的符號放置裝飾名稱就可以匯出整個類別。  MFC [DLLHUSK](http://msdn.microsoft.com/zh-tw/dfcaa6ff-b8e2-4efd-8100-ee3650071f90) 範例便用了這個方法。  
  
 雖然在這個方法中您不需要為類別建立 .def 檔和所有的裝飾名稱，但是建立 .def 檔卻是較有效率的方式，因為可以依序數匯出名稱。  若要使用 .def 檔來匯出，請將下列程式碼置於標頭檔的開頭和結尾：  
  
```  
#undef AFX_DATA  
#define AFX_DATA AFX_EXT_DATA  
// <body of your header file>  
#undef AFX_DATA  
#define AFX_DATA  
```  
  
> [!CAUTION]
>  匯出內嵌 \(Inline\) 函式時要特別小心，因為它們可能會產生版本衝突。  內嵌函式會展開至應用程式碼；因此，如果稍後您重寫函式，除非應用程式本身重新編譯，否則並不會將其更新   通常 DLL 函式可以更新，而無須重建使用它們的應用程式。  
  
## 匯出類別中的個別成員  
 有時您可能想要匯出類別的個別成員。  例如，如果您正在匯出 `CDialog` 衍生類別，您可能只需要匯出建構函式和 `DoModal` 呼叫。  您可以在需要匯出的個別成員上使用 **AFX\_EXT\_CLASS**。  
  
 例如：  
  
```  
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
  
 因為您不再匯出類別的所有成員，所以可能會因 MFC 巨集的使用方式而碰到其他問題。  有幾個 MFC 的 Helper 巨集實際上會宣告或定義資料成員。  因此，這些資料成員也必須從您的 DLL 匯出。  
  
 例如，建置擴充 DLL 時，`DECLARE_DYNAMIC` 巨集會定義如下：  
  
```  
#define DECLARE_DYNAMIC(class_name) \  
protected: \  
   static CRuntimeClass* PASCAL _GetBaseClass(); \  
public: \  
   static AFX_DATA CRuntimeClass class##class_name; \  
   virtual CRuntimeClass* GetRuntimeClass() const; \  
```  
  
 從 static `AFX_DATA` 開始的這行程式碼是在您的類別內部宣告一個靜態物件。  若要從用戶端可執行檔正確地匯出類別並存取執行階段資訊，您必須匯出這個靜態物件。  因為靜態物件已經用修飾詞 `AFX_DATA` 宣告，所以您在建置 DLL 時只需要將 `AFX_DATA` 定義成 **\_\_declspec\(dllexport\)**，而在建立用戶端可執行檔時定義為 **\_\_declspec\(dllimport\)**。  因為 **AFX\_EXT\_CLASS** 已經以這種方式定義，您只需要將 `AFX_DATA` 重新定義成與類別定義周圍 **AFX\_EXT\_CLASS** 相同的定義。  
  
 例如：  
  
```  
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
  
 因為 MFC 一定會在其巨集內部所定義的資料項目上使用 `AFX_DATA` 符號，所以這項技巧可用於所有這一類的案例。  例如，它可以用於 `DECLARE_MESSAGE_MAP`。  
  
> [!NOTE]
>  如果您是匯出整個類別而不是類別中選取的成員，則靜態資料成員會自動匯出。  
  
### 您想要執行甚麼工作？  
  
-   [使用 .def 檔從 DLL 匯出](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [使用 \_\_declspec\(dllexport\) 從 DLL 匯出](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
-   [匯出 C\+\+ 函式以用於 C 語言可執行檔](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)  
  
-   [匯出 C 函式以用於 C 或 C\+\+ 語言可執行檔](../build/exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)  
  
-   [判斷要使用哪一種匯出方法](../build/determining-which-exporting-method-to-use.md)  
  
-   [使用 \_\_declspec\(dllimport\) 匯入至應用程式](../build/importing-into-an-application-using-declspec-dllimport.md)  
  
-   [初始化 DLL](../build/initializing-a-dll.md)  
  
### 您還想知道關於哪些方面的詳細資訊？  
  
-   [裝飾名稱](../build/reference/decorated-names.md)  
  
-   [匯入和匯出內嵌函式](../build/importing-and-exporting-inline-functions.md)  
  
-   [交互匯入](../build/mutual-imports.md)  
  
## 請參閱  
 [從 DLL 匯出](../build/exporting-from-a-dll.md)