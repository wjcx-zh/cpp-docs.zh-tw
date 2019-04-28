---
title: TN026:DDX 和 DDV 常式
ms.date: 06/28/2018
f1_keywords:
- DDX
- DDV
helpviewer_keywords:
- DDX (dialog data exchange), procedures
- TN026
- DDV (dialog data validation), procedures
ms.assetid: c2eba87a-4b47-4083-b28b-e2fa77dfb4c4
ms.openlocfilehash: 89916e60d9677240f2d70e37e9a80e6ad7a76fc3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62305862"
---
# <a name="tn026-ddx-and-ddv-routines"></a>TN026:DDX 和 DDV 常式

> [!NOTE]
> 下列技術提示自其納入線上文件以來，未曾更新。 因此，有些程序和主題可能已過期或不正確。 如需最新資訊，建議您在線上文件索引中搜尋相關的主題。

此提示說明的對話方塊資料交換 (DDX) 和對話方塊資料驗證 (DDV) 架構。 此外，它也會說明如何撰寫一個 DDX_ 或 DDV_ 程序，以及如何擴充 ClassWizard 以使用您的常式。

## <a name="overview-of-dialog-data-exchange"></a>對話方塊資料交換的概觀

完成所有的對話方塊資料函式C++程式碼。 沒有任何特殊的資源或 magic 巨集。 虛擬函式，是類別中覆寫每個對話方塊中，沒有對話方塊資料交換和驗證機制的核心。 在這種形式一律找到它：

```cpp
void CMyDialog::DoDataExchange(CDataExchange* pDX)
{
    CDialog::DoDataExchange(pDX);   // call base class

    //{{AFX_DATA_MAP(CMyDialog)
        <data_exchange_function_call>
        <data_validation_function_call>
    //}}AFX_DATA_MAP
}
```

特殊格式 AFX 註解允許 ClassWizard 來找出並編輯中這個函式的程式碼。 ClassWizard 與不相容的程式碼應該會位於特殊格式註解。

在上述範例中， \<data_exchange_function_call > 的格式為：

```cpp
DDX_Custom(pDX, nIDC, field);
```

和\<data_validation_function_call > 是選擇性的格式為：

```cpp
DDV_Custom(pDX, field, ...);
```

中每個可能會包含一個以上的 DDX_/DDV_ 組`DoDataExchange`函式。

對話方塊資料交換常式和提供 MFC 對話方塊資料驗證常式的清單，請參閱 'afxdd_.h'。

對話方塊資料只是： 在成員資料`CMyDialog`類別。 它不會儲存在結構或任何類似項目。

## <a name="notes"></a>注意

雖然我們呼叫 「 對話方塊資料 」 時，所有功能都都可在任何衍生自的類別中`CWnd`並都不限於只是對話方塊。

標準中設定初始資料值的C++建構函式，通常在區塊中以`//{{AFX_DATA_INIT`並`//}}AFX_DATA_INIT`註解。

`CWnd::UpdateData` 是作業進行初始化和錯誤處理呼叫周圍`DoDataExchange`。

您可以呼叫`CWnd::UpdateData`隨時進行資料交換和驗證。 依預設`UpdateData`(TRUE) 稱為預設`CDialog::OnOK`處理常式並`UpdateData`(FALSE) 會呼叫預設`CDialog::OnInitDialog`。

DDV_ 常式應該緊接 DDX_ 常式針對該*欄位*。

## <a name="how-does-it-work"></a>如何運作

您不需要了解下列，才能使用對話方塊資料。 不過，了解如何將在幕後將協助您撰寫您自己的 exchange 或驗證程序。

`DoDataExchange`成員函式，就像`Serialize`成員函式-它會負責取得或設定資料至/來自外部的表單 （在此情況下控制項在對話方塊中） 從/至類別中的成員資料。 *PDX*參數是對進行資料交換內容，類似於`CArchive`參數來`CObject::Serialize`。 *PDX* (`CDataExchange`物件) 都有方向旗標很像`CArchive`方向旗標：

- 如果`!m_bSaveAndValidate`，然後載入控制項中的資料狀態。

- 如果`m_bSaveAndValidate`，然後設定從控制項的資料狀態。

只會發生驗證時`m_bSaveAndValidate`設定。 值`m_bSaveAndValidate`取決於 BOOL 參數`CWnd::UpdateData`。

有三個其他有趣`CDataExchange`成員：

- `m_pDlgWnd`：視窗 （通常的對話方塊），包含的控制項。 這是為了防止 DDX_ 和 DDV_ 全域函式的呼叫端来傳遞 'this' 每個 DDX/DDV 常式時。

- `PrepareCtrl`與`PrepareEditCtrl`:準備對話方塊控制項交換資料。 儲存該控制項的控制代碼設定焦點，如果驗證失敗。 `PrepareCtrl` 用於非編輯控制項和`PrepareEditCtrl`用於編輯控制項。

- `Fail`：將一個訊息方塊，提示使用者輸入錯誤之後呼叫。 這個常式會將焦點還原至最後一個控制項 (在上次呼叫`PrepareCtrl`或`PrepareEditCtrl`)，則擲回例外狀況。 可從 DDX_ 和 DDV_ 常式呼叫此成員函式。

## <a name="user-extensions"></a>使用者擴充功能

有數種方式來擴充預設的 DDX/DDV 機制。 您可以：

- 加入新的資料類型。

    ```cpp
    CTime
    ```

- 加入新的 exchange 程序 (DDX_)。

    ```cpp
    void PASCAL DDX_Time(CDataExchange* pDX, int nIDC, CTime& tm);
    ```

- 加入新的驗證程序 (DDV_)。

    ```cpp
    void PASCAL DDV_TimeFuture(CDataExchange* pDX, CTime tm, BOOL bFuture);
    // make sure time is in the future or past
    ```

- 將任意運算式傳遞至驗證程序。

    ```cpp
    DDV_MinMax(pDX, age, 0, m_maxAge);
    ```

    > [!NOTE]
    > 這類任意的運算式無法編輯 ClassWizard，因此應該移之外的特殊格式註解 (/ / {{AFX_DATA_MAP(CMyClass))。

已`DoDialogExchange`成員函式包含條件或任何其他有效的C++陳述式與混合的交換和驗證函式呼叫。

```cpp
//{{AFX_DATA_MAP(CMyClass)
DDX_Check(pDX, IDC_SEX, m_bFemale);
DDX_Text(pDX, IDC_EDIT1, m_age);
//}}AFX_DATA_MAP
if (m_bFemale)
    DDV_MinMax(pDX, age, 0, m_maxFemaleAge);
else
    DDV_MinMax(pDX, age, 0, m_maxMaleAge);
```

> [!NOTE]
> 如上所示，這類程式碼無法編輯 ClassWizard，應該用於只能之外的特殊格式註解。

## <a name="classwizard-support"></a>ClassWizard 支援

ClassWizard 會支援 DDX/DDV 自訂項目的子集，可讓您將自己 DDX_ 和 DDV_ 常式整合到 ClassWizard 使用者介面。 如果您打算重複使用特定 DDX 和 DDV 常式在專案中，或在許多專案中，執行此動作是有幫助的唯一成本。

若要這樣做，DDX 進行特殊的項目。CLW (舊版視覺效果的C++APSTUDIO 中儲存這項資訊。INI) 或您的專案中。CLW 檔案。 特殊的項目可以是輸入您的專案的 [一般資訊] 區段中。CLW 檔案或 [ExtraDDX] 區段的 DDX。\Program Files\Microsoft Visual Studio\Visual CLW 檔案C++\bin 目錄。 若要建立的 DDX。如果不存在，就會 CLW 檔案。 如果您打算只在特定專案中使用自訂的 DDX_/DDV_ 常式，加入您專案的 [一般資訊] 區段項目。CLW 改為檔案。 如果您打算使用的常式，在許多專案時，請 DDX [ExtraDDX] 區段中新增項目。CLW。

這些特殊的項目一般格式為：

> ExtraDDXCount=*n*

其中*n* ExtraDDX 數目嗎？ 若要遵循，表單的程式行

> ExtraDDX?=*keys*; *vb-keys*; *prompt*; *type*; *initValue*; *DDX_Proc* [; *DDV_Proc*; *prompt1*; *arg1* [; *prompt2*; *fmt2*]]

其中嗎？ 是一個數字 1- *n*指出在清單中所定義的 DDX 型別。

每個欄位是以 ';' 字元分隔。 如下所述的欄位，且其目的。

- *keys*

  指出此變數的類型允許的對話方塊控制項的單一字元的清單。

  |字元|允許的控制項|
  |-|-|
  E | 編輯
  C | 雙狀態核取方塊
  c | 三態核取方塊
  R | 在群組中的第一個選項按鈕
  L | 次序的清單方塊
  l | 已排序的清單方塊
  M | （與編輯項目） 的下拉式方塊
  N | 次序的下拉式清單
  n | 排序的下拉式清單
  1 | DDX 插入是否應該加入至清單的開頭 （預設為將新增到結尾） 這通常用來傳送 'Control' 屬性的 DDX 常式。

- *vb-keys*

  此欄位只適用於 16 位元產品 VBX 控制項 （VBX 控制項不支援在 32 位元產品中）

- *提示*

  將屬性的下拉式方塊 （沒有引號） 中的字串

- *type*

  發出標頭檔中的類型的單一識別項。 在上面的範例與 DDX_Time，這會設定為 CTime。

- *vb-keys*

  不會用於此版本，並應永遠為空白

- *initValue*

  初始值 — 0 或空白。 如果是空白的會將 //{{AFX_DATA_INIT 區段的實作檔中寫入沒有初始化行。 空白項目應該使用C++物件 (例如`CString`，`CTime`等等) 具有建構函式，確保正確地初始化。

- *DDX_Proc*

  DDX_ 程序的單一識別項。 C++函式名稱必須以"DDX_，"開頭，不過不會包含在 「 DDX_" \<DDX_Proc > 識別項。 在上面的範例， \<DDX_Proc > 識別項是時間。 當 ClassWizard 寫入函式呼叫中的實作檔案 {{AFX_DATA_MAP 區段中，它會附加此名稱至 DDX_，因此抵達 DDX_Time。

- *comment*

  在此 DDX 變數 對話方塊中顯示的註解。 將您想要在這裡，且通常提供項目描述的 DDX/DDV 組來執行的作業，任何文字。

- *DDV_Proc*

  DDV 部分的項目是選擇性的。 並非所有的 DDX 常式有相對應的 DDV 常式。 通常，它是更方便地納入不可或缺的一部分傳送的驗證階段。 這通常是當 DDV 常式不需要任何參數，因為 ClassWizard 不支援不含任何參數的 DDV 常式。

- *arg*

  DDV_ 程序的單一識別項。 C++函式名稱開頭必須是 「 DDV_"，但未包含"DDX_ 」 中的\<DDX_Proc > 識別項。

  *arg*後面 1 或 2 個 DDV 引數：

   - *promptN*

      將上方的編輯項目 （使用 & accelerator） 的字串。

   - *fmtN*

      做為引數類型，其中的格式字元：

      |字元|類型|
      |-|-|
      |d | int|
      |u | unsigned int|
      |D | long int （也就是，long）|
      |U | 長時間不帶正負號 (亦即，DWORD)|
      |f | float|
      |F | double|
      |秒 | 字串|

## <a name="see-also"></a>另請參閱

[依編號顯示的技術提示](../mfc/technical-notes-by-number.md)<br/>
[依分類區分的技術提示](../mfc/technical-notes-by-category.md)
