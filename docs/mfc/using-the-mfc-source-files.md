---
title: 使用 MFC 原始程式檔
ms.date: 08/19/2019
helpviewer_keywords:
- public members
- source files
- MFC, source files
- MFC source files
- comments, MFC
- private member access
- protected member access
- source files, MFC
ms.assetid: 3230e8fb-3b69-4ddf-9538-365ac7ea5e72
ms.openlocfilehash: ca5799da7a6ada42db20e3551b3fb7262e8990a0
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/20/2019
ms.locfileid: "69631672"
---
# <a name="using-the-mfc-source-files"></a>使用 MFC 原始程式檔

MFC 程式庫提供完整的原始程式碼。 標頭檔 (.h) 位於 *\atlmfc\include*目錄中。 執行檔 (.cpp) 位於 *\atlmfc\src\mfc*目錄中。

本文說明 MFC 用來批註每個類別之各個部分的慣例、這些批註的意義, 以及您在每個區段中應該會看到的內容。 Visual Studio 的嚮導會針對他們為您建立的類別使用類似的慣例, 而且您可能會發現這些慣例適用于您自己的程式碼。

您可能已熟悉**公用**、**受保護**和**私** C++用關鍵字。 在 MFC 標頭檔中, 您會發現每個類別可能會有其中的幾個。 例如, 公用成員變數和函數可能會在一個以上的**公用**關鍵字底下。 這是因為 MFC 會根據其使用來分隔成員變數和函式, 而不是依據允許的存取類型。 MFC 會謹慎使用**私**用。 即使是視為執行詳細資料的專案, 通常還是會**受到保護**, 而且許多次都是**公用**的。 雖然不鼓勵存取實作細節，但 MFC 將決定權保留給您。

在 mfc 應用程式精靈所建立的 MFC 原始程式檔和標頭檔中, 您可以在類別宣告 (通常是依此順序) 中找到如下的批註:

`// Constructors`

`// Attributes`

`// Operations`

`// Overridables`

`// Implementation`

## <a name="an-example-of-the-comments"></a>批註的範例

下列部分清單`CStdioFile`會使用 MFC 在其類別中採用的大部分標準批註, 以使用它們的方式來劃分類別成員:

```cpp
/*============================================================================*/
// STDIO file implementation

class CStdioFile : public CFile
{
    DECLARE_DYNAMIC(CStdioFile)

public:
// Constructors
    CStdioFile();

    // . . .

// Attributes
    FILE* m_pStream;    // stdio FILE
                        // m_hFile from base class is _fileno(m_pStream)

// Operations
    // reading and writing strings
    virtual void WriteString(LPCTSTR lpsz);
    virtual LPTSTR ReadString(_Out_writes_z_(nMax) LPTSTR lpsz, _In_ UINT nMax);
    virtual BOOL ReadString(CString& rString);

// Implementation
public:
    virtual ~CStdioFile();
#ifdef _DEBUG
    void Dump(CDumpContext& dc) const;
#endif
    virtual ULONGLONG GetPosition() const;
    virtual ULONGLONG GetLength() const;
    virtual BOOL Open(LPCTSTR lpszFileName, UINT nOpenFlags, CFileException* pError = NULL);

    // . . .

protected:
    void CommonBaseInit(FILE* pOpenStream, CAtlTransactionManager* pTM);
    void CommonInit(LPCTSTR lpszFileName, UINT nOpenFlags, CAtlTransactionManager* pTM);
};
```

這些批註會以一致的方式標示類別宣告的區段, 其中包含類似的類別成員類型。 請記住, 它們是 MFC 慣例, 而不是設定規則。

## <a name="-constructors-comment"></a>構造函式批註

MFC `// Constructors`類別宣告的區段會宣告函式 ( C++意義上), 以及實際使用物件所需的任何初始化函數。 例如, `CWnd::Create`位於 [函式] 區段中, 因為在您`CWnd`使用物件之前, 它必須先呼叫此C++函式, 然後呼叫`Create`函式, 以「完整結構化」。 一般而言, 這些成員是公用的。

例如, 類別`CStdioFile`有五個「函式」, 其中一個是顯示在 [[批註] 範例](#an-example-of-the-comments)底下的清單中。

## <a name="-attributes-comment"></a>屬性批註

MFC 類別宣告的 `// Attributes` 區段包含物件的公用屬性。 屬性通常是成員變數或取得/設定函數。 「Get」和「Set」函式不一定是虛擬的。 「Get」函式通常是**常數**, 因為在大部分的情況下, 它們不會有副作用。 這些成員通常是公用的。 受保護和私用屬性通常會在 [執行] 區段中找到。

在類別`CStdioFile`的範例清單中, 在[批註的範例](#an-example-of-the-comments)底下, 清單中會包含一個成員變數*m_pStream*。 `CDC` 類別幾乎列出此註解下的 20 個成員。

> [!NOTE]
> 大型類別 (例如 `CDC` 和 `CWnd`) 可能有許多成員在單一群組中列出所有屬性，但是不會很清楚。 在這種情況下，類別庫會使用其他註解作為標題，進一步描述成員。 例如，`CDC` 會使用 `// Device-Context Functions`、`// Drawing Tool Functions`、`// Drawing Attribute Functions` 等等。 表示屬性的群組會遵循上述的一般語法。 許多 OLE 類別都有稱為 `// Interface Maps` 的實作區段。

## <a name="-operations-comment"></a>作業批註

MFC `// Operations`類別宣告的區段包含成員函式, 您可以在物件上呼叫這些函式來進行作業或採取動作 (執行操作)。 這些函式通常不是**常數**, 因為它們通常會有副作用。 視類別的需求而定, 它們可能是虛擬或非虛擬的。 一般而言, 這些成員是公用的。

在來自類別`CStdioFile`的範例清單中, 在批註的範例中, 此清單會在此批註底下包含三個`WriteString`成員函[式](#an-example-of-the-comments): `ReadString`和的兩個多載。

如同屬性, 您可以進一步細分作業。

## <a name="-overridables-comment"></a>Overridables 批註

MFC 類別宣告的 `// Overridables` 區段含有當您需要修改基底類別行為時，您可以在衍生類別中覆寫的虛擬函式。 它們的名稱通常是以 "On" 為開頭, 但並不是絕對必要的。 此處的函式是專門用來覆寫，經常會實作或提供某種「回呼」或「攔截」。 一般來說，這些成員是受到保護的。

在 MFC 中，純虛擬函式一定會放置在此區段。 中C++的純虛擬函式採用下列格式:

`virtual void OnDraw( ) = 0;`

在類別`CStdioFile`的範例清單中, 在[批註的範例](#an-example-of-the-comments)中, 清單不包含 overridables 區段。 另一方面`CDocument`, 類別會列出大約10個可覆寫的成員函式。

在一些類別中，您也可能會看到 `// Advanced Overridables` 註解。 這些函式是只有先進的程式設計人員應該嘗試覆寫的函式。 您可能永遠都不需要覆寫它們。

> [!NOTE]
> 本文所述的慣例一般而言，也適合用於 Automation (先前稱為 OLE Automation) 方法和屬性。 Automation 方法與 MFC 作業類似。 Automation 屬性類似於 MFC 屬性。 Automation 事件 (支援 ActiveX 控制項，先前稱為 OLE 控制項) 與 MFC 可覆寫成員函式類似。

## <a name="-implementation-comment"></a>執行批註

`// Implementation` 區段是所有 MFC 類別宣告最重要的部分。

此區段包含所有實作詳細資料。 成員變數和成員函式二者可能都會出現在此區段中。 這一行以下的所有內容在 MFC 的未來版本中會有所變更。 除非您無法加以避免, 否則不應依賴這一行下方`// Implementation`的詳細資料。 此外, 在執行行底下宣告的成員尚未記載, 雖然在技術提示中會討論某些執行。 不論基類函式定義在哪個區段中, 覆寫基類中的虛擬函式都會在此區段中。 當函式覆寫基類執行時, 它會被視為「執行詳細資料」 (function)。 一般來說，這些成員是受到保護的，不過並不是始終受保護。

在`CStdioFile` [批註範例](#an-example-of-the-comments)底下的清單中, 在批註下方`// Implementation`宣告的成員可能會宣告為**public**、 **protected**或**private**。 請謹慎使用這些成員, 因為未來可能會變更。 可能需要將成員群組宣告為**公用**, 才能讓類別庫的執行正常運作。 不過, 這並不表示您可以安全地使用成員, 因此會宣告。

> [!NOTE]
> 您可能會在 `// Implementation` 註解的上方或下方找到剩餘類型的註解。 不論在上方或下方，它們會均描述在其下宣告的成員類型。 如果它們發生在 `// Implementation` 註解下，您應該假設成員在 MFC 的未來版本中可能會變更。

## <a name="see-also"></a>另請參閱

[一般 MFC 主題](../mfc/general-mfc-topics.md)
