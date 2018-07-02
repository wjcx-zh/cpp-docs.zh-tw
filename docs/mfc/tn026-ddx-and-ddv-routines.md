---
title: 'TN026: DDX 和 DDV 常式 |Microsoft 文件'
ms.custom: ''
ms.date: 06/28/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- DDX
- DDV
dev_langs:
- C++
helpviewer_keywords:
- DDX (dialog data exchange), procedures
- TN026
- DDV (dialog data validation), procedures
ms.assetid: c2eba87a-4b47-4083-b28b-e2fa77dfb4c4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 91b5d1a770dfd26db96b71179d3775003d7205c4
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/29/2018
ms.locfileid: "37122924"
---
# <a name="tn026-ddx-and-ddv-routines"></a>TN026：DDX 和 DDV 常式

> [!NOTE]
> 下列技術提示自其納入線上文件以來，未曾更新。 因此，有些程序和主題可能已過期或不正確。 如需最新資訊，建議您在線上文件索引中搜尋相關的主題。

此提示說明的對話方塊資料交換 (DDX) 和對話方塊資料驗證 (DDV) 架構。 它也會描述書寫一個 DDX_ 或 DDV_ 程序的方式，以及如何擴充 ClassWizard 若要使用您的常式。

## <a name="overview-of-dialog-data-exchange"></a>對話方塊資料交換的概觀

C + + 程式碼完成所有的對話方塊資料函式。 沒有任何特殊的資源或 magic 巨集。 機制的核心是虛擬函式，是類別中覆寫每個對話方塊，並對話方塊資料交換和驗證。 它一律是找到這種形式：

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

特殊格式 AFX 註解允許 ClassWizard 找出並編輯這個函式中的程式碼。 ClassWizard 與不相容的程式碼應該會位於外部的特殊格式註解。

在上述範例中，< data_exchange_function_call > 的格式為：

```cpp
DDX_Custom(pDX, nIDC, field);
```

和 < data_validation_function_call > 是選擇性的格式為：

```cpp
DDV_Custom(pDX, field, ...);
```

中每個可能會包含一個以上的 DDX_/DDV_ 組`DoDataExchange`函式。

對話方塊資料交換常式和對話方塊資料驗證常式隨 MFC 提供的清單，請參閱 'afxdd_.h'。

對話方塊資料僅是： 在成員資料`CMyDialog`類別。 它不會儲存在結構或類似的任何項目。

## <a name="notes"></a>注意

雖然我們呼叫 「 對話方塊資料 」 時，所有功能都都可在任何衍生自的類別中`CWnd`並都不限於只是對話方塊。

起始值的資料在標準 c + + 建構函式，通常是在含有的區塊中設定`//{{AFX_DATA_INIT`和`//}}AFX_DATA_INIT`註解。

`CWnd::UpdateData` 操作會進行初始化和錯誤處理的呼叫周圍`DoDataExchange`。

您可以呼叫`CWnd::UpdateData`隨時執行資料交換和驗證。 根據預設`UpdateData`(TRUE) 會呼叫預設`CDialog::OnOK`處理常式和`UpdateData`(FALSE) 會呼叫預設`CDialog::OnInitDialog`。

DDV_ 常式應該緊接 DDX_ 常式該*欄位*。

## <a name="how-does-it-work"></a>它如何運作

您不需要了解下才能使用對話方塊資料。 不過，了解如何將在幕後將協助您撰寫您自己的 exchange 或驗證程序。

`DoDataExchange`成員函式，就像`Serialize`成員函式-它會負責取得或設定資料至/從外部的表單 （在此情況下對話方塊中控制項） 來源/目的地類別中的成員資料。 *PDX*參數已經進行資料交換的內容，類似於`CArchive`參數`CObject::Serialize`。 *PDX* (`CDataExchange`物件) 的方向旗標很像`CArchive`方向旗標：

- 如果`!m_bSaveAndValidate`，然後將資料狀態載入控制項。

- 如果`m_bSaveAndValidate`，然後設定控制項中的資料狀態。

只會發生驗證時`m_bSaveAndValidate`設定。 值`m_bSaveAndValidate`BOOL 參數由`CWnd::UpdateData`。

有三個其他有趣`CDataExchange`成員：

- `m_pDlgWnd`: 包含的控制項 [] 視窗 （通常的對話方塊）。 這是為了避免 DDX_ 和 DDV_ 全域函式的呼叫端傳遞 'this' 的每個 DDX/DDV 常式時。

- `PrepareCtrl`與`PrepareEditCtrl`： 準備對話方塊控制項的資料交換。 儲存設定焦點，在驗證失敗時該控制項的控制代碼。 `PrepareCtrl` 用於非編輯控制項和`PrepareEditCtrl`來編輯控制項。

- `Fail`： 呼叫之後顯示訊息方塊，警示使用者輸入發生錯誤。 這個常式會將焦點還原到最後一個控制項 (在上次呼叫`PrepareCtrl`或`PrepareEditCtrl`)，則擲回例外狀況。 此成員函式可從 DDX_ 和 DDV_ 常式呼叫。

## <a name="user-extensions"></a>使用者擴充功能

有幾種方式來擴充預設的 DDX/DDV 機制。 您可以：

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

- 將任意的運算式傳遞至驗證程序。

    ```cpp
    DDV_MinMax(pDX, age, 0, m_maxAge);
    ```

    > [!NOTE]
    > 這類任意運算式 ClassWizard 無法編輯，因此應該移之外的特殊格式註解 (/ / {{AFX_DATA_MAP(CMyClass))。

具有`DoDialogExchange`成員函式包含條件式或具有混合的交換和驗證函式呼叫的任何其他有效的 c + + 陳述式。

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

ClassWizard 支援 DDX/DDV 自訂項目的子集，可讓您整合您自己 DDX_ 和 DDV_ 常式成 ClassWizard 使用者介面。 如果您打算重複使用的特定 DDX 和 DDV 常式在專案中或在許多專案中執行此動作是唯一的成本有幫助。

若要這樣做，DDX 中建立特殊的項目。CLW （舊版的 Visual c + + 會儲存在 APSTUDIO 這項資訊。INI) 或您的專案中。CLW 檔案。 特殊的項目可以是輸入您的專案的 [一般資訊] 區段中。CLW 檔案或 DDX [ExtraDDX] 區段中。CLW \Program Files\Microsoft Visual Studio\Visual C + + \bin 目錄中的檔案。 若要建立的 DDX。如果不存在的 CLW 檔案。 如果您打算使用自訂 DDX_/DDV_ 常式只能在特定專案中，加入您專案的 [一般資訊] 區段項目。CLW 檔案。 如果您打算使用的常式，在許多專案上，新增 DDX [ExtraDDX] 區段項目。CLW。

這些特殊的項目一般格式為：

> ExtraDDXCount =*n*

其中*n*是 ExtraDDX 數目嗎？ 若要依照，表單的線條

> ExtraDDX？ =*金鑰*;*vb 金鑰*;*提示*;*類型*;*initValue*;*DDX_Proc* [] 5d;*DDV_Proc*;*prompt1*;*arg1* [] 5d;*prompt2*;*fmt2*]]

位置嗎？ 是一個數字 1- *n*指出 DDX 類型所定義的清單中。

每個欄位是以 ';' 字元分隔。 如下所述的欄位，且其用途。

- *索引鍵*

  指出此變數的型別允許的對話方塊控制項的單一字元的清單。

  |字元|允許的控制項|
  |-|-|
  E | 編輯
  C | 雙狀態核取方塊
  c | 三種狀態核取方塊
  R | 在群組中的第一個選項按鈕
  L | 次序的清單方塊
  l | 已排序的清單方塊
  M | （與編輯項目） 的下拉式方塊
  N | 次序的下拉式清單
  n | 已排序的下拉式清單
  1 | 如果 DDX 插入應該加入至清單的開頭 （預設值加入結尾） 這通常用來傳輸 「 控制項 」 屬性的 DDX 常式。

- *vb 索引鍵*

  此欄位只能在 16 位元產品用於 VBX 控制項 （VBX 控制項不支援在 32 位元產品）

- *提示*

  將屬性的下拉式方塊 （沒有引號） 中的字串

- *type*

  標頭檔中發出的型別單一識別項。 在 DDX_Time 與上述範例，這會設定為 CTime。

- *vb 索引鍵*

  不使用在此版本中，而且應該永遠是空的

- *initValue*

  初始值-0 或空白。 如果是空白的沒有初始化列就會寫入 //{{AFX_DATA_INIT 部分實作檔案中。 空白項目適用於 c + + 物件 (例如`CString`，`CTime`等等)，具有建構函式，確保正確地初始化。

- *DDX_Proc*

  單一 DDX_ 程序的識別項。 C + + 函式名稱必須以"DDX_，"開頭，但不包含"DDX_"< DDX_Proc > 識別項中。 在上述範例中，< DDX_Proc > 識別項將時間。 當 ClassWizard 寫入函式呼叫中的實作檔案 {{AFX_DATA_MAP 區段中，附加這個名稱到 DDX_，因此抵達 DDX_Time。

- *comment*

  具有此 DDX 變數 對話方塊中顯示的註解。 將您想要在這裡，且通常提供項目描述的 DDX/DDV 組來執行的作業，任何文字。

- *DDV_Proc*

  DDV 部分的項目是選擇性的。 並非所有的 DDX 常式有對應的 DDV 常式。 通常，它是不可或缺的一部分傳送中包含驗證階段比較方便。 這是通常情況 DDV 常式不需要任何參數，因為 ClassWizard 不支援不含任何參數的 DDV 常式。

- *arg*

  單一 DDV_ 程序的識別項。 C + + 函式名稱開頭必須是"DDV_"，但是 < DDX_Proc > 識別項中不包含"DDX_"。

  *arg*後面接著 1 或 2 DDV 引數：

   - *promptN*

     若要將放在上方的編輯項目 (& accelerator) 的字串。

   - *fmtN*

     引數類型，其中的格式字元：

     |字元|類型|
     |-|-|
     d | int
     u | unsigned int
     D | long int （也就是，long）
     U | 長時間不帶正負號 (亦即，DWORD)
     f | float
     F | double
     秒 | 字串

## <a name="see-also"></a>另請參閱

[依編號顯示的技術提示](../mfc/technical-notes-by-number.md)  
[依分類區分的技術提示](../mfc/technical-notes-by-category.md)  
