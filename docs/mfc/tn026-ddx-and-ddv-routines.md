---
title: TN026：DDX 和 DDV 常式
ms.date: 06/28/2018
f1_keywords:
- DDX
- DDV
helpviewer_keywords:
- DDX (dialog data exchange), procedures
- TN026
- DDV (dialog data validation), procedures
ms.assetid: c2eba87a-4b47-4083-b28b-e2fa77dfb4c4
ms.openlocfilehash: 711d433b51ca09836f372d09a11f86c28b82cce6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370339"
---
# <a name="tn026-ddx-and-ddv-routines"></a>TN026：DDX 和 DDV 常式

> [!NOTE]
> 下列技術提示自其納入線上文件以來，未曾更新。 因此，有些程序和主題可能已過期或不正確。 如需最新資訊，建議您在線上文件索引中搜尋相關的主題。

本說明描述了對話框資料交換 (DDX) 和對話框數據驗證 (DDV) 體系結構。 它還描述了如何編寫DDX_或DDV_過程,以及如何擴展 ClassWizard 來使用例程。

## <a name="overview-of-dialog-data-exchange"></a>交談資料交換概述

所有對話框數據函數都使用C++代碼完成。 沒有特殊的資源或神奇的宏。 機制的核心是一個虛擬函數,該函數在每個執行數據交換和驗證的對話方塊類中都會被覆蓋。 它始終以此形式找到:

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

特殊格式的 AFX 註釋允許 ClassWizard 在此函數中尋找和編輯代碼。 與 ClassWizard 不相容的代碼應放置在特殊格式註釋之外。

在上面的示例中,data_exchange_function_call>\<的形式是:

```cpp
DDX_Custom(pDX, nIDC, field);
```

並且\<data_validation_function_call>是可選的,並且的形式是:

```cpp
DDV_Custom(pDX, field, ...);
```

每個`DoDataExchange`函數中可能包含多個DDX_/DDV_對。

有關 MFC 提供的所有對話數據交換例程和對話框數據驗證例程的清單,請參閱「afxdd_.h」。。

對話框資料就是:`CMyDialog`類中的成員數據。 它不存儲在結構或類似的東西中。

## <a name="notes"></a>注意

儘管我們稱之為"對話框數據",但所有功能都可用於派生自`CWnd`的任何類,並且不僅限於對話方塊。

數據的初始值設置在標準C++構造函數中,通常位於帶`//{{AFX_DATA_INIT`和`//}}AFX_DATA_INIT`註釋的塊中。

`CWnd::UpdateData`在 呼叫周邊執行初始化與錯誤處理的`DoDataExchange`操作 。

您可以隨時呼叫`CWnd::UpdateData`以執行資料交換和驗證。 預設情況下`UpdateData`,在預設`CDialog::OnOK`處理程式中調用 (TRUE),`UpdateData`並在`CDialog::OnInitDialog`預設值 中調用 (FALSE)。

DDV_例程應立即遵循該*字段*的DDX_例程。

## <a name="how-does-it-work"></a>它是如何工作的

使用對話框數據不需要瞭解以下內容。 但是,瞭解此操作方式將有助於確保您編寫自己的交換或驗證過程。

`DoDataExchange`成員函數與`Serialize`成員函數非常類似 - 它負責從類中的成員數據獲取或設置數據到/從外部窗體(在本例中為對話框中的控制項)。 *pDX*參數是執行資料交換的上下文`CArchive`,`CObject::Serialize`與的參數類似 。 *pDX(*`CDataExchange`物件 )具有非常`CArchive`類似於 具有方向標誌的方向標誌:

- 如果`!m_bSaveAndValidate`,則將數據狀態載入到控制項中。

- 如果`m_bSaveAndValidate`,則從控件設置數據狀態。

僅在設置驗證時`m_bSaveAndValidate`進行驗證。 的值`m_bSaveAndValidate`由 BOOL`CWnd::UpdateData`參數決定到 。

還有其他三個有趣的`CDataExchange`成員:

- `m_pDlgWnd`:包含控制項的視窗(通常是對話框)。 這是為了防止DDX_的調用方,DDV_全域函數必須將"此"傳遞給每個 DDX/DDV 例程。

- `PrepareCtrl`和`PrepareEditCtrl`:為數據交換準備對話方塊控制項。 存儲控件的句柄,用於在驗證失敗時設置焦點。 `PrepareCtrl`用於非編輯控制件,`PrepareEditCtrl`用於編輯控制項。

- `Fail`:在啟動一個消息框以提醒使用者輸入錯誤后調用。 此例程將焦點還原到最後一個控件(最後一個調用`PrepareCtrl``PrepareEditCtrl`或 ),並引發異常。 可以從DDX_和DDV_例程調用此成員函數。

## <a name="user-extensions"></a>使用者延伸

有幾種方法可以擴展預設的 DDX/DDV 機制。 您可以：

- 添加新數據類型。

    ```cpp
    CTime
    ```

- 添加新的交換過程(DDX_)。

    ```cpp
    void PASCAL DDX_Time(CDataExchange* pDX, int nIDC, CTime& tm);
    ```

- 添加新的驗證過程(DDV_)。

    ```cpp
    void PASCAL DDV_TimeFuture(CDataExchange* pDX, CTime tm, BOOL bFuture);
    // make sure time is in the future or past
    ```

- 將任意表達式傳遞給驗證過程。

    ```cpp
    DDV_MinMax(pDX, age, 0, m_maxAge);
    ```

    > [!NOTE]
    > 此類任意運算式不能由 ClassWizard 編輯,因此應移至特殊格式註釋之外(//{AFX_DATA_MAP(CMyClass))。

讓`DoDialogExchange`成員函數包括條件或任何其他有效的C++語句與混合交換和驗證函數調用。

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
> 如上所述,ClassWizard 不能編輯此類代碼,並且只能在特殊格式註釋之外使用。

## <a name="classwizard-support"></a>類別精靈支援

ClassWizard 允許您將自己的DDX_和DDV_例程整合到 ClassWizard 使用者介面中,從而支援 DDX/DDV 自定義的子集。 只有當您計劃在項目或許多專案中重用特定的 DDX 和 DDV 例程時,這樣做才具有成本效益。

為此,在 DDX 中製作特殊條目。CLW(早期版本的視覺C++將此資訊存儲在 APSTUDIO 中。INI)或您的項目的 。CLW 檔。 特殊項目可以在項目的 [常規資訊] 部分中輸入。CLW 檔案或 DDX 的 [額外DDX] 部分。CLW 檔在 [程式檔]微軟可視化工作室\視覺C++\bin 目錄中。 您可能需要創建 DDX。CLW 檔(如果不存在)。 如果計劃僅在特定專案中使用自定義DDX_/DDV_例程,請將條目添加到專案的 [常規資訊] 部分。而是 CLW 檔。 如果計劃在多個專案上使用例程,則將條目添加到 DDX 的 [ExtraDDX] 部分。CLW.

這些特殊項目目的一般格式是:

> 額外DDX( S) Count**n*

*n*是額外 DDX 的數量?行遵循,形式

> 額外DDX?**鍵*;*vb 鍵*;*提示*;*類型*;*initValue*;*DDX_Proc**DDV_Proc;**提示1;**arg1* *;*提示2;**fmt2*[]

哪裡? 是數位 1 - *n,* 指示正在定義的清單中鍵入哪個 DDX 類型。

每個欄位都由";"字元分隔。 下面將介紹欄位及其用途。

- *鑰匙*

  允許單個字元清單,指示此變數類型的對話方塊控制項。

  |字元|允許控制|
  |-|-|
  E | 編輯
  C | 雙狀態複選方塊
  c | 三州複選方塊
  R | 群組的第一個單選按鈕
  L | 未排序的清單框
  l | 序列表框
  M | 組合框 (包含編輯項目)
  N | 非排序的放置清單
  n | 排序放置清單
  1 | 如果 DDX 插入應添加到清單頭(預設添加到尾),這通常用於傳輸"控制"屬性的 DDX 例程。

- *vb 鍵*

  此欄位僅用於 VBX 控制檔的 16 位元產品(32 位元產品不支援 VBX 控制件)

- *提示*

  字串放在屬性組合框中(無引號)

- *型別*

  用於在標頭檔中發出的類型的單個標識碼。 在上面的DDX_Time示例中,這將設置為 CTime。

- *vb 鍵*

  此版本中未使用,應始終為空

- *initValue*

  初始值 = 0 或空白。 如果為空,則在實現檔的 //_AFX_DATA_INIT 部分不會寫入初始化行。 空白項目應用於具有保證正確初始化的構造函數`CString`C++`CTime`物件(如、等)。

- *DDX_Proc*

  DDX_過程的單個標識符。 C++函數名稱必須以"DDX_"開頭,但不要在\<DDX_Proc>標識符中包含"DDX_"。 在上面的示例中,DDX_Proc>\<標識符將是時間。 當 ClassWizard 將函數調用寫入 {AFX_DATA_MAP 節中的實現檔時,它將此名稱追加到DDX_,從而到達DDX_Time。

- *評論*

  註釋以在此 DDX 的變數對話框中顯示。 放置任何您喜歡的文字,通常提供描述 DDX/DDV 對執行的操作的內容。

- *DDV_Proc*

  條目的 DDV 部分是可選的。 並非所有 DDX 例程都有相應的 DDV 例程。 通常,將驗證階段作為傳輸的組成部分變得更加方便。 當 DDV 例程不需要任何參數時,通常會出現這種情況,因為 ClassWizard 不支援沒有任何參數的 DDV 例程。

- *精 氨 酸*

  DDV_過程的單個標識符。 C++函數名稱必須以"DDV_"開頭,但在\<DDX_Proc>標識符中不包括"DDX_"。

  *arg*後跟 1 或 2 DDV args:

  - *提示N*

      要放置在編輯項上方的字串(&用于加速器)。

  - *fmtN*

      arg 型態的格式字元,其中之一:

      |字元|類型|
      |-|-|
      |d | int|
      |u | 不帶正負號的整數|
      |D | 長因(即長)|
      |U | 長無符號(即DWORD)|
      |f | FLOAT|
      |F | double|
      |s | 字串|

## <a name="see-also"></a>另請參閱

[依編號顯示的技術提示](../mfc/technical-notes-by-number.md)<br/>
[依分類區分的技術提示](../mfc/technical-notes-by-category.md)
