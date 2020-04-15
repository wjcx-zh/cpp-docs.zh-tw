---
title: 視覺工作室C++示例
description: 存檔的 Visual Studio 中可用的範例的摘要說明 C++ GitHub 上的範例儲存庫。
ms.date: 03/23/2020
ms.technology: cpp-language
ms.assetid: 76798022-5886-48e7-a7f2-f99352b15cbf
ms.openlocfilehash: 0862f6b512f7278f878ade53b320ad5298bccf68
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "80215094"
---
# <a name="visual-studio-c-samples"></a>視覺工作室C++示例

可視化工作室C++示例可在 Web 上找到。 Microsoft 製作了許多C++示例,這些示例演示了跨多種技術的不同功能。 以下是一些查找其他範例的地方:

- [微軟文件範例 - C++](https://docs.microsoft.com/samples/browse/?term=c%2B%2B)

- [GitHub 上的 Windows 範例](https://microsoft.github.io/windows/)

- [Windows 開發人員中心代碼範例](https://developer.microsoft.com/windows/samples)

- [程式碼Plex範例](https://archive.codeplex.com/)

- [ADO 程式碼範例](/office/client-developer/access/desktop-database-reference/ado-code-examples-in-microsoft-visual-c)

- [Windows Hardware development samples](https://docs.microsoft.com/samples/browse/?products=windows-wdk) (Windows 硬體開發範例)

## <a name="archived-c-samples-on-github"></a>在 GitHub 上存檔C++範例

Visual Studio 在以前的版本中包含C++個範例代碼。 範例代碼要麼與Visual Studio一起安裝,要麼作為單獨的下載提供。 我們文檔中的許多文章都提到了這些範例。 它們不再被視覺工作室安裝。 相反,GitHub 上提供了一個存儲庫。 下表包含每個示例的說明,以及指向存儲庫中示例目錄的連結。

[!INCLUDE[note_security_samplecode](includes/note_security_samplecode_md.md)]

## <a name="atl-samples"></a>ATL 樣品

### <a name="atl-samples---advanced"></a>ATL 樣品 ─ 進階

| 範例名稱 | 描述 |
|--|--|
| [ActiveDoc](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/Advanced) | 示範如何實作主動式文件伺服程式 (Active Document Server)。 |
| [非同步](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/Advanced) | 從 URL 非同步載入資料。 |
| [ATLButton](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/Advanced) | 建立會根據本身狀態可顯示三種不同點陣圖的按鈕。 |
| [ATLDuck](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/Advanced) | 示範以 ATL 控制項使用連接點。 |
| [ATLSecurity](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/Advanced) | 顯示如何使用 ATL 安全類別來檢查安全設定。 |
| [ATLTraceTool](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/Advanced) | 顯示`ATLTRACE2`宏生成的輸出。 |
| [[連接]](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/Advanced) | 說明在多執行緒環境中連接點 (IConnectionPointContainer 和 IConnectionPoint 介面) 的實作與使用。 |
| [CThreadPool](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/Advanced) | 顯示如何在應用程式裡使用執行緒集區和實作執行緒集區如何改善應用程式的效能。 |
| [DCOM](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/Advanced) | 演示如何從多個用戶端調用在不同計算機上運行的 COM 物件(在 Windows 服務中實現)。 |
| [MFCATL](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/Advanced) | 說明 ATL COM 物件如何用於 MFC 伺服器 EXE。 |

### <a name="atl-samples---controls"></a>ATL 樣品 - 控制

| 範例名稱 | 描述 |
|--|--|
| [ATLFire](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/Controls) | 示範使用 ATL 建置視窗化控制項的方法。 |
| [CDInfo](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/Controls) | 播放 CD 音軌,並在工具提示和圓圖顯示中顯示有關軌道的資訊。 |
| [Circ](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/Controls) | 建立示範屬性頁和畫圓的控制項。 |
| [Polygon](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/Controls) | 建置實作自訂屬性 (Property)、事件、屬性頁和物件安全的控制項。 |
| [SubEdit](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/Controls) | 建立 Superclass 的 Windows 控制項。 |

### <a name="atl-samples---general"></a>ATL 樣品 - 一般

| 範例名稱 | 描述 |
|--|--|
| [ATLCollections](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/General) | 演示和`CComEnumOnSTL``ICollectionOnSTLImpl`的用法和以及自定義複製策略類的實現。 |
| [ATLCon](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/General) | 示範一個簡易控制項容器。 |
| [ATLSafeArray](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/General) | 展示如何使用`SAFEARRAY``CComSafeArray`建立與維護 s 。以及如何從元件傳遞到`SAFEARRAY`腳本。 |
| [AutoThread](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/General) | 演示使用`CComAutoThreadModule`類。 |
| [Beeper](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/General) | 實現集合/枚舉的`BSTR`分頁介面。 |
| [CircColl](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/General) | 實作使用 ATL 和 Standard C++ 程式庫之物件的集合/列舉型別 (Enumeration)。 |
| [COMMap](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/General) | 示範具有編譯器 COM 支援的 COM 介面對應項巨集。 |
| [CustomString](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/General) | 展示如何使用自定義記憶體分配器`CStringT`來提高多線程應用程式中的性能。 |
| [DispSink](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/General) | 示範在分派介面使用連接點。 |

### <a name="atl-samples---oledb---consumer"></a>ATL 樣品 - OLEDB - 消費者

| 範例名稱 | 描述 |
|--|--|
| [CatDB](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Consumer) | 顯示 OLE DB 提供者的結構描述資訊，例如表格和欄位。 |
| [DBViewer](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Consumer) | 演示一個中間級應用程式,該應用程式依賴於類`CManualAccessor`來完全控制應用程式的數據綁定。 |
| [DynamicConsumer](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Consumer) | 示範使用動態存取子和結構描述資料列集類別來讀取來自資料庫的中繼資料。 |
| [MultiRead](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Consumer) | 使用多個執行緒讀取資料庫中的資料表。 |

### <a name="atl-samples---oledb---provider"></a>ATL 樣品 - OLEDB - 提供者

| 範例名稱 | 描述 |
|--|--|
| [AdvancedPV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider) | 實現可更新的 OLE 資料庫提供程式。 示範一些進階的技巧。 |
| [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider) | 實現可更新(讀/寫)OLE 資料庫提供程式。 |

## <a name="clr-and-language-samples---windows-forms"></a>CLR 與語言範例 - Windows 表單

| 範例名稱 | 描述 |
|--|--|
| [BirthdayPicker](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/Language/Windows%20Forms) | 示範 .NET Framework 資源機制在 C++ 應用程式中的使用方式， 此外，本範例還會示範某些 Window Form 通用元件。 |
| [Calculator](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/Language/Windows%20Forms) | 使用 C++ 和 .NET Framework Windows Form 類別來實作簡單的袖珍計算機。 |
| 塗鴉(使用 MFC) | 實作 MFC 的 Scribble 範例，已經過更新和擴充以包含新的 .NET 功能。 |
| [Scribble (Windows Forms)](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/Language/General) | Scribble 範例的 Windows Form 實作，已更新並擴充成包含新的 .NET 功能。 |
| [STLCLR](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/CLR/stlclr/StlClr%20Sample) | 示範當使用 STL/CLR 程式庫時可用的某些功能。 |

## <a name="com-events-samples"></a>COM 事件範例

| 範例名稱 | 描述 |
|--|--|
| [COMEvents](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples) | 示範使用 COM 的事件處理。 |

## <a name="comtypelibfor7-samples"></a>ComTypeLibfor7 樣品

| 範例名稱 | 描述 |
|--|--|
| [ACDual](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ComTypeLibfor7) | 將雙重介面 (Dual Interface) 加入至 Automation 應用程式。 |
| [ADOSamp](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ComTypeLibfor7) | 實作三層 (Three-Tier) 的主從架構應用程式。 |
| [Allinone](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ComTypeLibfor7) | 在一個 MFC 應用程式中實作一個使用 ATL、公開 STL 集合物件並由編譯器 COM 支援控制的伺服程式。 |
| [COMMap](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ComTypeLibfor7) | 示範具有編譯器 COM 支援的 COM 介面對應項巨集。 |
| [[連接]](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ComTypeLibfor7) | 說明瞭連接點(和`IConnectionPointContainer``IConnectionPoint`介面)在多線程環境中的使用和實現。 |
| [DCOM](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ComTypeLibfor7) | 演示如何從在不同計算機上運行的多個用戶端調用 COM 物件(在 Windows 服務中實現)。 |
| [FreeThrd](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ComTypeLibfor7) | 示範一個多重執行緒用戶端和具有編譯器 COM 支援的無限制執行緒伺服程式。 |
| [InProc](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ComTypeLibfor7) | 示範具有編譯器 COM 支援的同處理序 (In-Process) Automation 伺服器應用程式。 |
| [Labrador](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ComTypeLibfor7) | 實現沒有任何用戶介面的 EXE 伺服器。 |
| [MFCCalc](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ComTypeLibfor7) | 示範一個具有編譯器 COM 支援的 Automation 伺服器應用程式。 |

## <a name="compiler-samples"></a>編譯器範例

### <a name="compiler-samples---general"></a>編譯器範例 ─ 一般

| 範例名稱 | 描述 |
|--|--|
| [ccWrapper](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/Compiler) | 示範如何將其他編譯器的 C/C++ 編譯器旗標對應到 Visual C++ 編譯器 (cl.exe)。 |

### <a name="compiler-samples---masm"></a>編譯器範例 - MASM

| 範例名稱 | 描述 |
|--|--|
| [EuclidStep1](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/Compiler/MASM) | 這是一個純 C 專案，示範使用 Euclid 的演算法來找出最大公因數。 |
| [歐幾裡德步驟2](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/Compiler/MASM) | 歐幾裡德Step1的擴展,它是一個混合的C和MASM專案。 歐幾*`.c`* 裡德演演算法的核心從*`.asm`* 檔案移動*`.c`* 到 檔案,*`.asm`* 檔案呼叫到 檔案中。 |
| [PrimesStep1](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/Compiler/MASM) | 一個純粹的C專案,演示伊拉托塞內斯的篩子,以找到質數。 |
| [PrimesStep2](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/Compiler/MASM) | PrimesStep1 的副檔名,它是將核心演*`.asm`* 算法移動到 檔案中的混合 C 和 MASM 專案。 |
| [PrimesStep3](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/Compiler/MASM) | PrimesStep2 的副檔名,用於添加單獨的*`.asm`* C 標頭 檔和一個包含檔,用於聲明外部函數和全域資料結構。 |

## <a name="crt-samples"></a>CRT 樣品

| 範例名稱 | 描述 |
|--|--|
| [CPUID](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt) | 判斷正在執行之 CPU 的效能。 |
| [CRT_Dbg1](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt) | 說明 C 執行階段程式庫的基本偵錯功能。 |
| [CRT_Dbg2](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt) | 示範 C Run-Time 偵錯攔截函式。 |
| [DFACObjs](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt) | 顯示如何使用 _CrtDoForAllClientObjects C 執行階段函式來重複執行用戶端物件的連結串列。 |
| [Report](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt) | 說明 C Run-Time 偵錯回報函式。 |
| [RTC](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt) | 示範執行階段錯誤檢查功能。 |
| [SecureCRT](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt) | 這個範例示範如何將使用已取代的 CRT 功能的程式碼升級，增加程式碼安全性。 |

## <a name="debugging-samples"></a>除錯範例

| 範例名稱 | 描述 |
|--|--|
| [EEAddIn](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples) | 這個函式會使用運算式評估工具增益集 (Expression Evaluator Add-In) API 來擴充原生 (Native) 偵錯工具的運算式評估工具。 |

## <a name="fusion-samples"></a>融合樣品

| 範例名稱 | 描述 |
|--|--|
| [TraceMan](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples) | 以人類可讀形式提供有關與應用程式相關的程式集以及本機融合緩存中的程式集狀態的資訊。 |

## <a name="hilo-sample"></a>希洛樣品

| 範例名稱 | 描述 |
|--|--|
| [希洛](https://github.com/Microsoft/VCSamples/tree/master/VC2013Samples/Hilo) | Hilo 是一系列文章和示例應用。 它們展示了 Windows 7、Visual Studio 和C++構建高性能、回應式用戶端應用程式的能力。 Hilo 提供原始碼和指導,可説明您設計和開發您自己的引人注目的、支援觸控的 Windows 應用程式。<br/><br/>此示例已更新為 Visual Studio 2013。 它包括*AsyncLoaderMemory Manager.cpp*檔(第 36 行和第 37 行)的熱修復,該檔解決了常見的崩潰問題。 |

## <a name="international-samples"></a>國際樣品

| 範例名稱 | 描述 |
|--|--|
| [IME](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/International) | 示範如何控制輸入法 (IME) 模式，以及如何實作 IME 層級 3。 |
| [SatDLL](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/International) | 示範在 Win32 應用程式中實作多語系資源的建議方式。 |
| [UniRes](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/International) | 示範 Unicode 資源檔的用法。 |

## <a name="language-samples---general"></a>語言範例 ─ 一般

| 範例名稱 | 描述 |
|--|--|
| [Data](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/Language) | 示範 SQL 資料庫的簡單存取。 |
| [MEDriver](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/Language) | 其中將說明如何透過由 COM 伺服器型別程式庫自動產生的 .NET Framework 包裝函式來使用 COM 事件 (從 Unmanaged COM 伺服器引發)。 |
| [Nile](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/Language) | 演示ASP.NET Web 窗體和ASP.NET Web 服務。 |
| [QStat](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/Language/General) | 示範如何建立一個可包裝 COM 物件存取權限、並向 .NET Framework 用戶端公開其功能的 DLL。 |
| [Scribble](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/Language/General) | 示範如何使用 C++/CLI 和 .NET Framework 類別來開發 Windows Form MDI 應用程式。 |
| [TilePuzzle](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/Language/General) | 示範 Managed 元件 (以 C++ 和 C# 撰寫) 和原生元件 (以採用 COM 屬性的 C++ 所撰寫) 之間的互通性。 |

## <a name="mfc-samples"></a>MFC 範例

### <a name="mfc-samples---advanced"></a>MFC 樣品 ─ 進階

| 範例名稱 | 描述 |
|--|--|
| [Collect](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced) | 示範 MFC C++ 範本架構的集合類別以及標準的預先建置集合類別。 |
| [立方體](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced) | 使用 MFC 裝置內容和 OpenGL 資源內容的 OpenGL 應用程式。 |
| [DLLHusk](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced) | 提供 MFC 程式庫的 DLL 版本給應用程式和自訂的 DLL 共用。 |
| [DLLScreenCap](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced) | 一個可以靜態或動態連結到 MFC 程式庫之規則 DLL。 |
| [MTGDI](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced) | 示範使用架構對文件與檢視的單一文件介面 (SDI) 支援，在多個執行緒間共用 GDI 資源。 |
| [MTMDI](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced) | 說明多執行緒，其中使用介面事件可以在不同的使用介面執行緒中處理。 |
| [MTRecalc](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced) | 多線程圖,其中在工作線程中完成重新計算。 |
| [Mutex](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced) | 基於對話框的應用程式,創建兩`CWinThread`個物件,並使用它們在使用者控制下執行任務。 |
| [Speakn](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced) | 使用使用者定義的資源演示多媒體聲音。 |

### <a name="mfc-samples---controls"></a>MFC 樣品 - 控制

| 範例名稱 | 描述 |
|--|--|
| [Button](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/controls) | 演示使用就地活動功能表、股票屬性頁和"關於"框控制項選項。 |
| [Circ](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/controls) | 演示 ActiveX 控制基礎知識。 其中包括控制項繪製、股票和自訂屬性、股票和自訂事件、顏色和字型的使用、股票字體屬性頁、預設屬性頁和版本控制。 |
| [CmnCtrl](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/controls) | 展示在 wiprlhext 上可以使用 MFC 的新控制器:`CButton`命令連結按鈕 ()、尋呼`CPagerCtrl`器`CSplitButton`控制件 ()、 拆`CNetAddressCtrl`分按鈕 () 和網路 位址控制件 ()。 |
| [Contain](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/controls) | 示範視覺化編輯容器應用程式。 |
| [影像](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/controls) | 演示如何使用 MFC 構建以非同步方式下載資料的 ActiveX 控制件。 |
| [許可](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/controls) | 一個強制設計階段和執行階段授權使用的控制項。 |
| [Localize](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/controls) | 一個當地語系化使用者介面的控制項，它將展示用於當地語系化之個別型別程式庫和資源動態聯結程式庫 (DLL) 的使用方式。 |
| [NetAddr](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/controls) | 示範 Windows Vista「網路位址驗證器」控制項的用法。 |
| [朋友](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/controls) | 會顯示調色盤色彩的控制項。 它會示範唯讀屬性、永續性 Get/Set 屬性、永續性參數化屬性以及圖片屬性。 |
| [推送](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/controls) | 從 Windows 主控描繪按鈕控制項子類別化的控制項。 它會示範內建屬性、自訂事件和圖片位置。 |
| [RegSvr](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/controls) | 示範自我登錄程式碼的引動過程。 |
| [SpinDial](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/controls) | 一個擁有微調撥號視覺外觀的控制項，可展示屬性頁資料驗證。 |
| [TestHelp](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/controls) | 一個擁有自己的說明檔案和工具提示的 ActiveX 控制項。 |
| [時間](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/controls) | 一個在執行階段不可見，且會在設定的時間間隔引發計時器事件的控制項。 示範告知功能和環境屬性 (Ambient Property)。 |
| [X 清單](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/controls) | 一個從 Windows 清單方塊子類別化、可顯示文字或點陣圖項目的控制項。 |

### <a name="mfc-samples---general"></a>MFC 樣品 ─ 一般

| 範例名稱 | 描述 |
|--|--|
| [ClipArt](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | ClipArt 目錄包含可用於自訂應用程式外觀的範例資源。 |
| [CmnCtrl1](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 示範如何使用 MFC 類別來建立和變更 Windows 通用控制項的樣式 (第一部分)。 |
| [CmnCtrl2](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 示範如何使用 MFC 類別來建立和變更 Windows 通用控制項的樣式 (第二部分)。 |
| [C 工作交談](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 演示`CTaskDialog`類的各種功能。 |
| [CtrlBars](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 自訂工具列、狀態列、對話方塊列和浮動工具板。 |
| [CtrlTest](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 主控描繪的清單方塊、功能表、自訂控制項、點陣圖按鈕和微調控制項。 |
| [DBVList](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 使用`CListView`和`CDaoRecordset`類實現可用於清單檢視公共控制項的虛擬清單檢視功能。 |
| [DIBLook](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 示範 DIB 和色板的用法。 |
| [DlgCbr32](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 將工具列和狀態列加入至對話方塊架構應用程式。 |
| [DlgTempl](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 示範動態建立對話方塊範本。 |
| [DockTool](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 可停靠的拖動和浮動工具列。 |
| [Dynamenu](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 動態修改功能表的項目清單；處理編譯時間未知的命令；並且更新這類命令的狀態列命令提示字元。 |
| [FileDlgWatcher](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 建立自訂對話框,說明建立 時產生的`CFileDialog`事件 。 |
| [你好](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 示範具有功能表和 [關於] 對話方塊的單一應用程式視窗。 |
| [HelloApp](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 最小的 MFC 範例，示範讓視窗顯示於畫面上所需的數行程式碼。 |
| [ListHdr](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 展示如何使用公共控制程式 MFC`CListCtrl``CHeaderCtrl`類別與 。 |
| [MDI](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 不使用文件和檢視的 MDI 應用程式。 |
| [MDIDocVw](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 使用文件/檢視架構的更新版 MDI 範例。 |
| [MMXSwarm](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 展示如何使用`CImage`資料`__m64`類型和設備無關的點陣圖 (DIB)。 |
| [模 態](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 演示使用 MFC`CDialog`物件作為無模式對話方塊。 |
| [Multipad](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 簡單的文字編輯器，可讓使用者同時開啟及編輯多個文字檔。 |
| [Npp](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 演示如何實現類似於記事本的介面 (SDI) 應用程式。 它允許您編輯文本消息,並通過 Windows 消息 API 或 MAPI 將它們發送給其他使用者或其他系統。 |
| [PropDlg](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 屬性工作表 (對話方塊)。 |
| [RowList](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 說明清單檢視通用控制項中的整列選取。 |
| [Scribble](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 簡單示範 MFC 強大的功能。 |
| [SimpleImage](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 示範載入、調整大小、轉換和儲存影像。 |
| [SnapVw](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 展示如何在 MDI 子框架視窗中使用屬性頁。 |
| [Spiro](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 顯示要使用的`CImageList`遊戲以及如何在需要動畫效果的應用程式中使用記憶體顯示上下文的遊戲。 |
| [Tracker](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 展示各種`CRectTracker`樣式和選項。 |
| [VariantUse](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 示範 Variant 資料型別的用法。 |
| [ViewEx](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general) | 多個檢視、捲動檢視、分隔視窗。 |

### <a name="mfc-samples---internet"></a>MFC 樣品 - 網路

| 範例名稱 | 描述 |
|--|--|
| [DHTMLExplore](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/internet) | 展示處理 DHTML 事件和使用 DHTML DDX。 |
| [HTMLEdit](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/internet) | 包裝 Internet Explorer MSHTML 編輯器控制項。 |
| [MFCIE](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/internet) | 演示 MFC`CHtmlView``CReBar`和類。 |
| [排程器](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/internet) | 示範如何使用 Visual C++ 程式庫類別建立 HTML 架構對話方塊。 |

### <a name="mfc-samples---ole"></a>MFC 樣品 - OLE

| 範例名稱 | 描述 |
|--|--|
| [ACDual](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/ole) | 示範如何將雙重介面支援加入至一個 MFC 架構的 Automation 伺服應用程式。 |
| [AutoClik](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/ole) | 說明 Automation 功能。 包含 AUTODRIV 這個可以驅動 AUTOCLIK 範例應用程式的簡單用戶端應用程式。 |
| [CalcDriv](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/ole) | Automation 用戶端。 |
| [DrawCli](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/ole) | 全功能的物件導向繪圖應用程式，同時也是一個 ActiveX 視覺化編輯容器。 |
| [HierSvr](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/ole) | 示範伺服器應用程式與 OLE 拖放。 |
| [InProc](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/ole) | 一個可當成 DLL 載入於用戶端位址空間的同處理序 Automation 伺服程式。 |
| [IPDrive](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/ole) | 一個驅動 INPROC 範例應用程式的簡單 Automation 用戶端應用程式。 |
| [MFCBind](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/ole) | 示範如何建立主動式文件 (即是先前的 DocObject) 容器。 |
| [MFCCalc](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/ole) | 一個實作簡易的計算機的 Automation 伺服程式。 |
| [OClient](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/ole) | 可以執行拖放的 ActiveX 視覺化編輯容器應用程式。 |
| [OLEView](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/ole) | 透過自訂的 OLE 介面來實作一個 OLE 物件瀏覽器。 |
| [SuperPad](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/ole) | 展示使用 CEditView 編輯文字的視覺化編輯伺服器。 |
| [TstCon](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/ole) | 使用 OLE 內嵌的 MFC 支援來實作一個 ActiveX 控制項容器。 您可以使用 TSTCON 來測試 ActiveX 控制項、變更其屬性和叫用其方法。 |
| [寫字板](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/ole) | 使用 Rich Edit 控制項的 MFC 支援來建立一個基本的文字處理器。 |

### <a name="mfc-samples---utility"></a>MFC 樣品 ─實用程式

| 範例名稱 | 描述 |
|--|--|
| [GUIDGen](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/utility) | 一種基於對話框的簡單 MFC 應用程式,可生成全域唯一標識符。 |
| [Makehm](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/utility) | 產生資源識別與說明主題代碼 (Help Context) 之間對應的主控台應用程式 (Console Application)。 |

### <a name="mfc-samples---visual-c-2008-feature-pack"></a>MFC 樣品 - 視覺C++ 2008 功能套件

| 範例名稱 | 描述 |
|--|--|
| [CustomPages](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 示範如何將自訂頁面加入至工具列自訂對話方塊。 |
| [DesktopAlertDemo](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 演示如何實現桌面警報對話框(類似於即時訊息應用程式的對話方塊)。 |
| [DlgToolTips](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 示範如何為對話方塊上的控制項實作進階工具提示。 |
| [DrawClient](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 展示如何透過編輯容器支援將功能區的支援整合到繪圖應用程式中。 |
| [DynamicMenu](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 示範如何在執行階段動態更新功能表列上的功能表和快顯功能表。 |
| [探險 家](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 展示如何實現類似於檔案資源管理員的檔案系統資源管理員。 它具有類似的用戶介面元素和功能。 |
| [IEDemo](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 示範如何實作與 Internet Explorer 類似、具有類似使用者介面項目和功能的應用程式。 |
| [MDITabsDemo](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 示範如何建立使用新索引標籤式 MDI 文件介面 (而非傳統 MDI 子視窗) 的應用程式。 |
| [MenuSubSet](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 示範如何在應用程式啟動時動態移除特定功能表項目和子功能表。 |
| [MSMoneyDemo](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 示範如何使用 MFC 建立與 Microsoft Money 類似的使用者介面。 |
| [MSOffice2007Demo](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 示範如何實作與 Office 2007 應用程式類似、具有類似使用者介面項目和類似有限功能的編輯器應用程式。 MSOffice2007Demo 示例實現了完整的功能區用戶介面,與Office 2007 應用程式類似。 某些功能區元素連接到應用程式中的功能。 |
| [NewControls](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 演示 MFC 中實現的許多控制項的功能。 這些控制項包括可自訂按鈕、顏色選取器控制器、調色板、字型選擇器、影像編輯器、屬性網格、遮罩編輯控制件以及 shell 清單和樹控件。 |
| [OutlookDemo](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 示範如何建立與 Outlook 2003/2007 類似的應用程式。 |
| [OutlookMultiViews](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 示範如何在 SDI 應用程式中對單一文件切換多個檢視。 本範例使用 Outlook 功能區控制項列出可用的檢視，以及在這些檢視之間進行切換。 |
| [OwnerDrawMenu](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 說明如何動態描繪快顯功能表項目。 |
| [PaletteDemo](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 示範如何建立具有主控描繪資訊區域的多欄工具列。 按一下標準工具列上的 2、3 或 4 個按鈕,以在執行時更改自訂工具列的欄數。 |
| [PropSheetDemo](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 示範下列類型的屬性工作表控制項：簡單、索引標籤於左側、樹狀目錄控制項於左側、OneNote 樣式索引標籤、項目清單於左側。 |
| [RebarTest](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 演示承載工具列的可自定義鋼筋控件。 |
| [RibbonGadgets](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 示範可裝載於功能區控制項的各種控制項。 在主框架的底部,您可以找到帶有原始程式碼文本的原始程式碼視窗,該視窗概述了如何創建特定小工具。 |
| [RibbonMDI](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 示範功能區控制項搭配多重文件介面的用法。 |
| [RollupPane](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 示範會自動向上捲動的浮動「資訊」窗格。 您可以按下浮動窗格標題的固定按鈕，開啟和關閉捲動功能。 |
| [SetPaneSize](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 示範如何以程式設計方式設定停駐窗格大小。 |
| [Slider](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 示範如何實作裝載外部控制項的工具列按鈕。 |
| [StateCollection](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 示範如何實作一個會儲存及載入功能表列、工具列和停駐視窗不同狀態的應用程式。 |
| [StatusBarDemo](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 示範如何將各種進階控制項加入至狀態列。 |
| [TabbedView](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 示範如何建立包含多個索引標籤式檢視的檢視，例如 Excel 活頁簿中的索引標籤。 |
| [TabControl](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 示範 MFC 索引標籤控制項，以及使用不同屬性和視覺管理員時其不同的外觀。 |
| [TasksPane](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 示範 MFC 工作窗格類別，以及使用各種屬性和視覺管理員時其不同的外觀。 |
| [ToolbarDateTimePicker](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 示範如何將日期/時間選擇器控制項與工具列整合。 |
| [ToolTipDemo](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 示範如何使用進階 MFC 工具提示功能。 |
| [TrayMenu](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 說明瞭使用帶有系統托盤圖示的 MFC 控制條功能表的能力。 它類似於顯示器右下角的通知圖示。 |
| [VisualStudioDemo](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 演示如何使用 Visual Studio 的許多相同的使用者介面特性和功能實現應用程式。 演示了許多 Visual Studio 用戶介面元素,包括可自定義的停靠功能表欄、工具列和視窗。 |
| [寫字板](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 示範如何實作模仿 WordPad 功能 (包括使用者介面項目及部分功能) 的應用程式。 |
| [WorkSpaceToolBar](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/Visual%20C%2B%2B%202008%20Feature%20Pack) | 示範如何將工具列加入至停駐窗格。 它類似於視覺化工作室中的解決方案資源管理器中的工具列。 |

### <a name="mfc-samples---windows-touch"></a>MFC 樣品 - Windows 觸控

| 範例名稱 | 描述 |
|--|--|
| [GestureDemo](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/WindowsTouch) | 示範 MFC 中的 Windows Touch 支援 (需要觸控硬體)。 |
| [TouchDemo](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/WindowsTouch) | 示範 MFC 中的 Windows Touch 支援 (需要觸控硬體)。 |

## <a name="odbc-samples"></a>ODBC 樣品

| 範例名稱 | 描述 |
|--|--|
| [奧布恰](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/ODBC%20Database%20sample) | 此示例展示如何使用ODBC API連接到和訪問資料庫。 |

## <a name="os-samples"></a>作業系統樣本

| 範例名稱 | 描述 |
|--|--|
| [GetImage](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples) | 示範 Windows 影像擷取 (WIA) 應用程式開發介面 (Application Programming Interface，API)。 |

## <a name="unix-samples"></a>Unix 樣本

| 範例名稱 | 描述 |
|--|--|
| [Unix - ccWrapper](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples) | 示範會將 Sun Forte 和 gcc 編譯器的旗標對應到 Microsoft Visual C++ 編譯器 (cl.exe) 的包裝函式。 |

## <a name="windows-8-samples"></a>Windows 8 範例

Windows 8 示例包包括為 Windows 8 開發和更新的所有應用代碼示例。 示例包提供了一種一次下載所有樣品的便捷方法。 此示例包中的範例有 C#、C++、VB.NET 和 JavaScript。 Windows 示例庫包含代碼範例,用於練習 Windows 8 和 Windows Server 2012 中提供的各種新程式設計模型、平臺、功能和元件。 這些可下載的範例包含可視化 Studio 解決方案 (*sln*) 檔案、 源檔案、 資產、 資源和中繼資料,以便成功編譯和執行。

有關每個範例中展示的程式設計模型、平臺、語言和 API 的詳細資訊。 請參閱 Windows 8 文檔中提供的指南、教程和參考文章,請參閱 Windows 開發人員中心。 這些示例是全天候提供的,以演示 Windows 8 和 Windows Server 2012 的程式設計模型和功能 API 的功能。

| 範例名稱 | 描述 |
|--|--|
| [背景傳輸範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示了 Windows 運行時應用程式後台傳輸 API 的電源友好、成本感知和靈活行為。 提供的範例方案涵蓋檔下載和上載。 |
| [加密 WinRT 範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用新的加密 API。 |
| [列印範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何應用整合 Windows 列印體驗。 此示例中演示的方案包括:使用超級按鈕欄和列印協定從應用列印、應用體驗中列印等。 |
| [HTTPClient 範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例展示使用 HTTPClient 類別和 IXMLHTTPRequest2 介面使用 Windows 執行時提供的網路功能從 HTTP 伺服器上載和下載各種類型的內容。 |
| [加速度計感應器樣品(Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用`Windows.Devices.Sensors.Accelerometer`API。 此示例允許使用者查看沿 X 軸、Y 軸和 Z 軸的 3 軸加速度計的加速度力。 您可以選擇三種方案之一。 |
| [帳號圖片名稱範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例演示了獲取當前登錄的使用者名稱的不同方法。 它還演示如何獲取和設置用於使用者磁貼的圖像。 |
| [套用設定範例(Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例展示如何使用應用程式設定 API 和設定彈出視窗將應用的設定 UI 與「設定」超級按鈕整合。 這個範例使用`Windows.UI.ApplicationSettings`命名空間`WinJS.UI.SettingsFlyout`與 。 |
| [在相機示例的 Windows 應用商店裝置應用 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何為攝像機創建 Windows 應用商店設備應用。 Windows 應用商店設備應用由IHV或OEM提供,以區分特定攝像機的拍攝體驗。 |
| [開始C++簡單的部落格閱讀器範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 該示例演示了本機C++使用 XAML 定義使用者介面的本機C++ Windows 應用商店應用開發的一些基本原則。 它是 Windows 開發人員中心上討論的應用程式的完整工作版本。 |
| [讀取與寫入資料範例(Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用DataReader和DataWriter類來存儲和檢索資料。 |
| [應用程式資料範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例展示如何使用 Windows 執行時應用程式數據 API 儲存和檢索特定於每個使用者和 Windows 應用商店應用的數據。 應用程式數據包括會話狀態、使用者首選項和其他設置。 |
| [自訂驅動程式存取範例(Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例展示如何使用 CreateDeviceAccessA 和 IDeviceIoControl 存取專用裝置。 |
| [XAML 清單檢視與格格檢視要點範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例展示如何使用 GridView 和 ListView 控制件。 |
| [動畫指標範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何在 中`Windows.UI.Core`使用 動畫指標 API。用於造訪定義 Windows 動畫庫中動畫的原始參數的動畫指標。 |
| [播放管理器 msAudio 類別範例(Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何為音訊視頻 (AV) 流選擇正確的 msAudio 類別,將其配置為音訊播放流。 |
| [XAML DirectX 3D 射擊遊戲範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示了在C++應用程式中使用 DirectX(Direct3D 11.1、Direct2D、XInput 和 XAudio2)和 XAML 實現的簡單第一人稱三維遊戲。 XAML 用於抬頭顯示和遊戲狀態消息。 |
| [XAML 滾動、平移和縮放範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用ScrollViewer控制項平移和縮放。 |
| [XAML 翻轉檢視控制項範例(Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例展示如何使用 FlipView 控制件使用戶能夠翻轉集合。 |
| [陀螺儀感測器樣品(視窗 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用`Windows.Devices.Sensors.Gyrometer`API。 此示例允許使用者查看沿 X 軸、Y 軸和 Z 軸的 3 軸陀螺儀的角度速度。 |
| [印表機 SDK 範例的裝置應用 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何為可以從磁貼協定、printTask 設定協定以及後台任務顯示的 Toast 以回應列印驅動程式事件的印表機創建設備應用。 |
| [背景工作範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用 Windows 運行時後台任務 API 創建和註冊後台任務。 後台任務由系統或時間事件觸發,並且可以受一個或多個條件的約束。 |
| [串流通訊字示例(Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示了使用 Windows 運行時提供的網路功能的 StreamSocket 類的基礎知識。 範例的用戶端元件創建 TCP 套接字以建立網路連接、使用套接字發送數據等。 |
| [計畫通知範例(Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例展示如何為應用使用計畫磁貼更新和定期磁貼更新和 Toast 通知。 此功能使您能夠指定提供通知的精確時間,即使應用未運行也是如此。 |
| [播放管理員來配套範例(Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何為音訊視頻流選擇正確的 msAudio 類別,以將其配置為音訊播放流。 |
| [定向感應器範例(Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用`Windows.Devices.Sensors.OrientationSensor`API。 它允許使用者查看反映當前設備方向的旋轉矩陣和四元值。 |
| [檔案存取範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何建立、讀取、寫入、複製和刪除檔、如何檢索文件屬性以及如何追蹤檔或資料夾以便應用可以再次訪問該檔。 此範例使用`Windows.Storage`和`Windows.Storage.AccessCache`API。 |
| [可移動儲存範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 可移動儲存範例展示如何將檔案傳輸到可行動存放裝置或從可行動存放裝置傳輸檔。 此示例需要連接到系統的可移動存放裝置,如相機、媒體播放器、行動電話或 USB 拇指驅動器。 |
| [XAML 表面影像來源 DirectX 互通範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例展示如何使用`SurfaceImageSource`在 XAML 應用中包含 DirectX 內容。 此示例同時使用C++和 C#。 |
| [連接 WebSocket 範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例展示如何在連接的 Windows 應用商店應用中使用 WebSocket。 該示例介紹了基本功能,例如如何建立連接、發送和接收數據以及關閉連接。 |
| [為媒體範例設定金鑰(Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何在鍵盤上配置硬體媒體鍵。 然後,如何使用配置的鍵通過按或單擊播放、暫停、停止等來控制音訊視頻流。 |
| [XAML 個性動畫範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何在應用中使用內置的個性動畫。 |
| [Toast 通知範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用 Toast 通知:螢幕右上角顯示為彈出式通知的通知。 用戶可以選擇 Toast(觸控或單擊)以啟動關聯的應用。 |
| [聯絡人選取器應用程式範例(Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例展示如何使用聯絡人選取器選擇一個或多個連絡人。 它還包括聯繫人選取器 API 的基本實現,以演示如何向使用者顯示聯絡人清單。 |
| [DirectX 大理石迷宮遊戲範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例展示如何使用 DirectX 建構基本 3D 遊戲。 這個遊戲是一個簡單的迷宮遊戲,玩家面臨的挑戰是滾動大理石通過迷宮的陷阱使用傾斜控制。 |
| [DirectX 明信片應用程式範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示了使用 DirectX 與 C++使用 DirectX 和 XAML 互通創建明信片時使用 DirectX 和 XAML 創建的簡單 Windows 應用商店應用的實現。 |
| [DirectX 3D 射擊遊戲範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示了在C++應用程式中使用 DirectX(Direct3D 11.1、Direct2D、XInput 和 XAudio2)實現的簡單第一人稱三維遊戲。 |
| [XAML 應用程式控制圖例(Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例展示如何使用 AppBar 控制件向使用者顯示導航、命令和工具。 默認情況下,應用欄處於隱藏狀態,當使用者從螢幕頂部或底部邊緣輕掃手指時,將顯示應用欄。 |
| [日期與時間格式範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例展示如何在`Windows.Globalization.DateTimeFormatting`命名空間中使用 DateTimeFormatter 類根據使用者的首選項顯示日期和時間。 |
| [協助磁貼範例(Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何固定和使用輔助磁貼。 這是一個磁貼,可直接存取應用中的特定非預設部分或體驗,例如已保存的遊戲或社交網路應用中的特定好友。 |
| [輸入觸控控測試範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例使用多邊形形狀拼圖來演示如何處理指標輸入、實現觸控輸入的自定義命中測試以及使用 C++ 和 DirectX 在 Windows 應用商店應用中處理操作。 |
| [網路資訊範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用 Windows 運行時網路資訊 API。 |
| [輸入簡化墨跡範例(Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何在 Windows 應用商店應用中使用墨蹟功能。 |
| [儲存資料來源與取得虛擬化檔案Vector範例(Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何在用戶的圖片庫中檢索和顯示圖像。 |
| [基於邊緣的手勢呼叫範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用`EdgeGesture`類偵聽在基於邊緣的 UI 中發生的事件。 |
| [檢查目前工作階段是否為遠端範例(Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示了 API`Windows.System.RemoteDesktop`的使用。 |
| [應用程式資源與本地化範例(Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用應用程式資源將可本地化內容與應用程式代碼分開。 這個範例使用`Windows.ApplicationModel.Resources.Core`與`Windows.Globalization`命名空間`WinJS.Resources`與 。 |
| [內容選單範例(Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例展示如何建立上下文選單以及如何取代文本的預設上下文選單。 此示例使用`Windows.UI.Popups`API,包括彈出功能表和上下文選單事件。 |
| [地理位置範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 地理位置範例展示如何使用地理位置 API 取得使用者 PC 的地理位置。 應用可以使用地理位置 API 獲取位置一次,也可以持續跟蹤位置。 |
| [訊息對話框範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例展示如何使用 MessageDialog 顯示對話方塊、設定命令及其操作以及更改預設按鈕。 命名`Windows.UI.Popups`空間包含消息對話類。 |
| [MediaStream源媒體擴展示例(Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何在 Windows 應用商店應用中支援 Microsoft Silverlight MediaStreamSource 概念。 |
| [直接寫入垂直文字範例(Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例使用 DirectWrite 和 Direct2D 在自訂佈局形狀中正確顯示垂直文本。 |
| [DXGI 交換鏈旋轉範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示了 IDXGISwapChain1::setRotation 方法,以及如何將該方法與預旋轉內容結合使用以提高演示性能。 |
| [Direct2D 自訂影像效果範例(Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用標準圖元、頂點和計算底影實現自定義 Direct2D 效果。 |
| [DirectX 觸控輸入範例(Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示了使用 Direct3D 的C++應用中的三維環境的觸摸和滑鼠導航。 |
| [X輸入遊戲控制器範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示了在C++應用中使用 Xinput API。 它讀取來自 Xbox 遊戲控制器的輸入,並顯示有關模擬鬥桿移動和按鈕按下的數據。 |
| [直接 3D-直接 2D 互通範例(Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何與 Direct2D 和 DirectWrite 進行互通,以將文本寫入 Direct3D 渲染目標。 它是創建抬頭顯示器和基於文本的讀出(如遊戲和三維應用中的評分面板)的有效方法。 |
| [以範例(Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示了 Windows 8 的基本 Windows 應用商店應用,該應用可以從 Web 服務檢索源。 此示例目前以 JAVAScript、C#、C++ 和 VB 程式設計語言提供。 |
| [套用磁貼和徽章範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用應用磁貼,該磁貼是"開始"螢幕中應用的表示和啟動點。 它還演示如何在該磁貼上使用徽章。 它是應用在應用未運行時向使用者中繼狀態資訊的方法。 |
| [XAML 使用者與自訂控制項範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例展示如何建立和使用 XAML`UserControl`元素並為專案建立自訂控制件。 |
| [Direct3D 資源載入範例(Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示了使用 DirectX C++應用的 Direct3D 資源載入。 |
| [XAML 清單檢視和格格檢視自訂互動性範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示了控制項的`ListView`互動模型。 |
| [XAML WebView 控制件範例(Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例展示如何使用 控制`WebView`器顯示網址、載入 HTML、與 中的`WebView`文`WebViewBrush`稿互動以及使用 。 |
| [指南針感應器樣品(視窗 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用`Windows.Devices.Sensors.Compass`API。 此示例允許使用者將指南針讀數視為磁北讀數,並根據已安裝的感測器將讀取為真北值。 |
| [顯示方向範例(Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用`DisplayProperties`類 在應用中設置顯示方向。 |
| [直接 2D 插值模式範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例顯示了 Direct2D 使用的各種插值模式。 |
| [全球化偏好設定範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用`Windows.System.UserProfile.GlobalizationPreferences`類 獲取使用者的全球化首選項。 它還演示如何使用`GeographicRegion`和`Language`類。 |
| [Direct2D 幾何實現範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例顯示多核幾何鑲嵌如何説明減少幾何渲染時間。 使用不一致蒙版和模因是傳統幾何渲染的替代方法,在某些情況下可能更好。 |
| [語言字型對應範例(Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用命名空間中的`LanguageFontGroup`類獲取特定於語言`Windows.Globalization.Fonts`的 字體建議。 |
| [自測儀感測器樣品(視窗 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用`Windows.Devices.Sensors.Inclinometer`API。 此示例允許使用者查看 3 軸傾斜計的 X 軸、Y 軸和 Z 軸的傾斜角度。 |
| [XAML 高對比度樣式範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示了在應用中實現高對比度模式支援的各種技術。 支援高對比度模式對於使有視力問題的人訪問你的應用非常重要。 |
| [輸入裝置功能範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何查詢連接到使用者設備的輸入設備。 以及如何支援 Windows 應用商店應用的指標、觸摸、筆/觸筆、滑鼠和鍵盤輸入模式。 |
| [郵件用戶端範例的 EAS 政策 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例展示如何郵件客戶端檢索設備資訊並處理提供的 Exchange 活動同步 (EAS) 策略。 Windows 應用商店應用可以配置其郵件用戶端以保持與給定的 EAS 策略一樣。 |
| [資料格拉姆 Socket 表示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示了使用 Windows`DatagramSocket`運行時 提供的網路功能的類基礎知識。 範例的用戶端元件創建UDP套接字,使用套接字發送和接收資料,並關閉套接字。 |
| [直接寫你好世界範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例展示如何使用 DirectWrite 和 Direct2D 將文字「Hello`CoreWindow`World」呈現給 。 |
| [壓縮範例(Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何從檔中讀取結構化數據並將壓縮數據寫入新檔,以及如何讀取壓縮數據和將解壓縮數據寫入新檔。 許多應用程式需要壓縮和解壓縮數據。 |
| [網路狀態背景範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例展示如何透過使用 Internet 存在條件註冊網路狀態更改事件的後台任務處理程式來確定 Internet 連接設定檔中的更改。 |
| [套用套件資訊範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用 Windows 運行時打包 API 獲取包資訊。 用戶獲取 Windows 應用商店應用作為應用包。 Windows 使用應用包中的資訊按使用者安裝應用。 |
| [光感應器樣品 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用`Windows.Devices.Sensors.LightSensor`API。 此示例允許用戶將環境光讀數視為 LUX 值。 您可以選擇以下兩種方案之一:光感測器數據事件、電流光感測器讀數等。 |
| [移動寬頻帳戶預配範例(Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例展示如何使用 Windows 8 行動寬頻預配代理`Windows.Networking.NetworkOperators.ProvisioningAgent`API ( ) 設定 Windows 8 具有所需的連接資訊和存取預配。 |
| [媒體播放到範例(Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示了"播放到 API」。。 它顯示了如何擴展媒體應用程式,將視頻、音訊和圖像流式傳輸到本地網路上的其他設備。 |
| [輸入觸控鍵盤範例(Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何在未從平臺控制項派生的自定義控制項中自動啟動觸控鍵盤。 該示例實現需要鍵盤輸入且不派生自標準 XAML 控制件的自定義控制項。 |
| [XAML 動畫函式庫範例(Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何為元素設置動畫,以及如何對動畫應用緩動函數以實現各種效果。 |
| [捕捉範例(Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 捕捉狀態是四種可能的應用程式視圖狀態之一。 捕捉應用將應用大小調整到 320 像素寬,這允許它與其他應用共享螢幕。 捕捉使兩個應用同時可見。 |
| [轉碼媒體範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用`Windows.Media.Transcoding`API 在 Windows 應用商店應用中對影片檔進行轉碼。 轉碼是數位媒體檔案 (例如視訊或音訊檔案) 的轉換，也就是從一種格式變成另一種格式。 |
| [XAML 二維變換範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用二維變換來修改元素在應用中的顯示方式。 「轉換」定義了如何將點從一個座標空間對應或轉換到另一個座標空間。 |
| [IXmlReader 和 IXmlWriter XML 資料讀取寫入範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何在 Windows`IXmlReader``IXmlWriter`應用商店 應用中使用 C++。 它們用於從平面 XML 格式的文本檔中讀取和寫入 XML 資料。 這些介面是 Windows Win32 和 COM API 的一部分,但受 Windows 執行時的支援。 |
| [使用擷取裝置範例進行媒體擷取 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用`MediaCapture`API 從捕獲設備(如網路攝像機)捕獲視頻、音訊和圖片。 |
| [XAML 彈出式範例(Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例展示如何在專案中建立和使用 XAML 彈出視窗元素。 |
| [相機擷取資訊範例(Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用`Windows.Media.Capture.CameraCaptureUI`API,該 API 顯示用於捕獲照片或視頻的全屏 UI。 相機捕獲 UI 提供從照片切換到影片的控制項、用於拍攝延遲時間照片的計時器等。 |
| [XAudio2 音訊檔播放範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示了在應用中使用 XAudio2。 |
| [希洛C++樣品 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用C++和 XAML 構建完整的 Windows 應用商店應用。 Hilo 照片示例為希望使用現代C++、XAML 和 Windows 運行時創建 Windows 8 應用的C++開發人員提供了指南。 |
| [直接寫入自訂文字呈現器範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何實現 DirectWrite 的自訂文本呈現器。 |
| [直接寫入字型枚舉示例(Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例展示如何使用 DirectWrite 在使用者裝置上列出系統字體集合中的字型。 |
| [Direct2D 透視轉換圖示例(Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用`DrawBitmap`API 顯示應用透視轉換的圖像。 |
| [相機選項 UI 範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何在設備應用中使用攝像機選項。 API`CameraOptionsUI`顯示用於調整攝像機設置的 UI。 此示例需要網路攝像頭。 |
| [X輸入音訊控制器播放範例(Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示了對應用中 XInput 設備(如耳機)的 XAudio2 播放。 |
| [Direct2D 3D 變換效果範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示了在三維空間中轉換圖像的不同方法。 |
| [Windows 帳號授權範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用`Windows.Security.Authentication.OnlineId`命名空間的成員在委派模式下使用其 Microsoft 帳戶對使用者進行身份驗證。 以及如何使用 REST 協定將獲取的權杖發送到即時連接 API。 |
| [數位格式設定與分析範例(Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例`DecimalFormatter`示範如何`CurrencyFormatter``PercentFormatter``Windows.Globalization.NumberFormatting`在命名空間中使用、`PermilleFormatter`類。 它們用於顯示和分析數位、貨幣和百分比值。 |
| [DXGI 提供與資源回收資源範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例展示使用 DirectX 在`IDXGIDevice2::OfferResources`C++`IDXGIDevice2::ReclaimResources`應用中 使用 DXGI 和 API。 |
| [Web 認證代理範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示 Web 身份驗證代理 WinRT API。 它允許您啟用與 OAuth 供應商(如 Facebook、Google、微軟和 Twitter)的單一登錄 (SSO) 連接。 |
| [XAudio2 音效串流效果範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例使用 XAudio2 和媒體基礎 API 演示C++應用程式中的音訊流。 |
| [飛濺畫面範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例展示如何在 Windows 關閉其顯示的初始螢幕時正確定位類似影像,從而模仿 Windows 為應用顯示的初始螢幕。 |
| [簡訊後臺任務範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例展示如何使用 Windows 8 行動寬頻`Windows.Devices.Sms`SMS API`Windows.ApplicationModel.Background`( ) 與後台 任務 API ( ) 一起發送和接收 SMS 文本訊息。 |
| [簡訊傳送、接收和 SIM 管理範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用 Windows 8 移動寬頻`Windows.Devices.Sms`SMS API ()。 |
| [試用應用和應用內購買範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用 Windows 應用商店提供的許可 API 來確定應用或應用內購買啟用的功能的許可狀態。 |
| [輸入觸控鍵盤文字輸入範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何在觸摸鍵盤上啟用優化的視圖。 它的工作原理是使用輸入作用域和輸入類型與命名空間中的`WinJS.UI`控制項以及`TextBox`和`RichEdit`XAML 控制項。 |
| [XAML 文字編輯範例(Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例展示如何在應用中使用文字輸入控制項。 |
| [執行緒池示例(Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用 Windows 運行時線程池 API 非同步執行工作項。 |
| [UI 自動化核心視窗提供者範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例展示如何創建Microsoft UI自動化提供程式。 它使有關 Windows 應用商店應用的程式設計資訊可供可存取的技術(如螢幕閱讀器)使用。 該示例為 Direct2D 應用程式。 |
| [XAML 輔助功能範例(Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何向應用添加基本輔助功能支援。 |
| [播放列表示例(Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例展示如何建立、儲存、顯示和編輯音訊檔的播放清單。 此示例使用命名空間中的`Windows.Media.Playlists`類。 |
| [媒體伺服器客戶端範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用媒體伺服器 API 創建媒體伺服器用戶端。 媒體伺服器示例演示如何在本地網路上以程式設計方式流覽數位媒體伺服器,並顯示其所有視頻檔。 |
| [Direct2D 雜誌應用範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例展示如何使用 Direct2D、DirectWrite、Windows 映像元件 (WIC) 和 XAML 構建具有雜誌類型演示文稿的應用。 |
| [移動寬頻帳戶和裝置管理範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例展示如何使用行動網路營運商 (MNO) 使用的`Windows.Networking.NetworkOperators`Windows 8 行動寬頻 API ( ) 。 它演示如何使用行動寬頻帳戶 API 來檢索和顯示可用的行動寬頻帳戶。 |
| [鄰近範例(Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用`PeerFinder``ProximityDevice`和 類與附近的計算機進行通信。 您可以使用 API`Proximity`在點擊手勢期間交換小消息,或在對等應用之間設置套接字連接。 |
| [建立 Windows 執行時行程內元件範例 (C++CX) (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何在C++/CX 中創建用於C++/CX、JavaScript 和C# 用戶端代碼的元件。 OvenServer 專案包含一個名為`Oven`的 運行時類,`IOven`它實現了一`IAppliance`個介面和一個介面。 |
| [裝置自動旋轉偏好設定範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用`DisplayProperties`類來處理和驗證設備旋轉事件。 |
| [即時通訊示例(Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用低延遲功能啟用即時通信應用程式。 |
| [分享內容來源應用程式範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何應用與其他應用共享內容。 此示例使用命名空間中的`Windows.ApplicationModel.DataTransfer`類。 |
| [搜尋合約範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何允許使用者在選擇「搜尋」超級按鈕並打開搜索窗格時搜索你的應用。 以及如何使用搜索窗格來顯示使用者查詢的建議。 |
| [原始通知範例(Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用原始通知,原始通知是推送通知,沒有執行應用後台任務的關聯 UI。 |
| [Direct2D 基本影像效果範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何載入影像、對影像應用高斯模糊效果,然後在`Windows::UI::Core::CoreWindow`中顯示圖像。 |
| [對基元範例的直接 2D 效果 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例展示如何將影像效果應用於 Direct2D 基元。 此示例使用 Direct2D 繪製圓角矩形,然後在矩形中間繪製 DirectWrite 文字。 然後,它應用效果圖。 |
| [控制通道觸發流套接字示例(Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 該示例演示如何在`ControlChannelTrigger`Windows 應用商店應用中使用類。 它使用 TCP,`StreamSocket`因此應用程式始終連接且始終可到達。 此示例演示了後台網路通知的使用。 |
| [控制通道觸發流 Web 套接字示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 該示例演示如何使用`ControlChannelTrigger`類 使使用 StreamWebSocket 的 Windows 應用商店應用始終連接且始終可訪問。 此示例演示了後台網路通知的使用。 |
| [關聯啟動範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何啟動檔類型或協定的預設應用。 您還可以瞭解如何使應用成為檔案類型或協定的預設應用。 |
| [原子Pub範例(Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例簡報如何從 Web 存取、創建、更新和刪除聯合內容來源。 它使用 Atom 發佈標準的 Windows 運行時實現。 |
| [憑證註冊範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例展示如何在認證層次結構中創建和註冊證書。 要獲取 Windows 8 的評估副本,請轉到 Windows 8。 要獲取 Microsoft Visual Studio 2012 的評估副本,請轉到 Visual Studio 2012。 |
| [剪貼簿應用範例(Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何應用使用剪貼簿命令,包括複製、粘貼、剪切和移動。 此示例使用命名空間中的`Windows.ApplicationModel.DataTransfer`類。 |
| [Direct2D 複合效果模式範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例顯示了 Direct2D 提供的多種複合和混合模式。 |
| [Direct3D 凹凸映射範例(Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示了使用普通貼圖和每圖元照明繪製的凹凸貼圖。 |
| [行事曆詳細資訊和數學範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例展示如何使用命名空間中的`Calendar``Windows.Globalization`類根據日曆系統和使用者的全球化首選項操作和處理日期。 |
| [裝置列舉示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用設備枚舉 API 尋找可用裝置並查找設備資訊。 該示例介紹兩種方案:在第一個方案中,設備枚舉 API 用於查找特定的設備介面。 |
| [直接寫入段落文字範例(Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例展示如何使用 DirectWrite 與 Direct2D 將段`CoreWindow`落文字呈現給 。 並且,對佈局應用對齊和字元間距。 |
| [回應螢幕鍵盤範例 (Windows 8) 的外觀](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | [本文檔是初步文檔,可能會更改。此示例演示如何偵聽和回應螢幕軟鍵盤的外觀。 當焦點提供給在沒有鍵盤的設備上需要文本輸入的元素時。 |
| [XAML 資料繫結圖樣範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示了使用綁定類和綁定標記擴展的基本數據綁定技術。 |
| [Direct3D 教程範例(Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例是一個五課教程。 它提供了 Direct3D API 的介紹,並介紹了許多其他 DirectX 範例中使用的概念和代碼。 |
| [Direct2D 效果相片調整應用程式範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例顯示了使用 Direct2D 效果的各種常見照片操作技術。 此示例分為幾個部分。 第 1 課:使用 Direct2D 效果顯示載入和繪製圖像的基礎知識。 |
| [Windows 音訊工作階段 (WASAPI) 範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 演示如何使用 Windows 音訊作業階段 API (WASAPI) 執行各種音訊相關任務。 |
| [使用者名稱範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示命名空間`UserInformation`類`Windows.System.UserProfile`提供的與域相關的功能。 "使用者資訊"類使應用能夠獲取和設置有關使用者的資訊。 |
| [USSD 訊息管理範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示了使用 USSD 協定與支援 GSM 的行動寬頻裝置的網路帳戶管理。 USSD 通常用於行動網路營運商 (MNO) 對行動寬頻配置檔的帳戶管理。 |
| [必應地圖行程最佳化器範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 該示例演示如何使用 JAVAScript 和 VisualC++,以及如何為名為必應地圖旅行優化器的 Windows 8 創建應用。 必應地圖行程優化器使用 JAVAScript 來定義 UI,並並行C++計算成本高昂的演演演算法。 |
| [在路徑範例(Windows 8) 上直接 2D 和直接寫入動畫文字](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用 Direct2D 和 DirectWrite 沿動畫非線性幾何路徑呈現文本字串。 該應用程序呈現"你好,世界! 沿貝塞爾曲線使用不同的語言重複幾次。 |
| [Wi-Fi 熱點身分驗證範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例展示如何使用 Windows 8 行動寬`Windows.Networking.NetworkOperators`頻 API 進行 Wi-Fi 熱點身分驗證。 使用此機制作為為 Wi-Fi 熱點配置靜態憑據的替代方法。 |
| [XAML 影像範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示了使用圖像控制件和 BitmapImage 類在應用中顯示和操作圖像的各種技術。 |
| [主頁組應用範例(Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例示範如何使用`HomeGroup`打開、搜索和共用檔。 這個範例使用與中的`HomeGroup``Windows.Storage.Pickers`一些選項`Windows.Storage.KnownFolders`。 |
| [UI 對比與設定範例(Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例展示如何在基本 C# 或 JavaScript 應用中使用 UI 設定 API。 |
| [資料夾列舉示例(Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例展示如何列出位置內的頂級檔案和資料夾。 (例如,資料夾、設備或網路位置。並且,如何使用查詢將檔分類到檔組中來列出位置內的所有檔。 |
| [檔案選取器範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例展示如何透過允許使用者透過檔案選取器選擇檔案和資料夾來存取它們。 以及如何儲存檔案,以便使用者可以指定要儲存的檔案的名稱、檔案類型和位置。 |
| [檔案選取器協定範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例展示如何透過檔取取器向其他應用提供檔、儲存位置和即時檔更新。 它通過參與檔打開選取器協定、檔保存選取器協定和緩存檔更新程式協定來完成。 |
| [程式設計檔案搜尋範例(Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例展示如何在資料夾、庫、設備或網路位置等位置查詢檔。 它使用`Windows.Storage.Search`API。 此示例中的重要 API`QueryOptions`包括:`StorageFileQueryResult`類、 類別和其他。 |
| [檔案與資料夾縮圖示例(Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何檢索檔和資料夾的縮略圖。 它使用`Windows.Storage.FileProperties`API。 |
| [輸入操作與手勢 (C++) 範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例展示如何使用 C++ 和 DirectX 處理`GestureRecognizer`Windows 應用商店 應用中的 API 中的指標輸入和處理操作和手勢。 |
| [Direct3D HLSL 分形發生器樣本 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例展示使用 Direct3D HLSL 和 DirectCompute 計算掃描器創建分形影像。 |
| [XAML 直接 2D 照明效果範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示了 Direct2D 效果中可用的照明效果。 照明效果屬性由 XAML 介面控制件控制,然後透過 XAML 交換鏈背景面板使用 Direct2D 顯示。 |
| [Direct2Dapp 列印範例(Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何將 Direct2D 列印支援添加到 Windows 應用商店應用。 此示例演示如何使用 Direct2D 功能呈現用於列印的 Windows 應用商店應用的內容。 以及如何將呈現的內容發送到印表機。 |
| [直接 2D 列印影像與效果範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何在 Windows 應用商店應用中列印 Direct2D 圖像和 Direct2D 效果。 |
| [Direct2D 動畫文字範例(Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例展示如何使用 Direct2D`FillOpacityMask`方法快速呈現文本。 該示例還回應觸摸。 兩個手指捏合可用於放大和縮小文本。 |
| [直接3D後處理效果範例(Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示了使用縮小的中間緩衝區在簡單旋轉立方體場景中進行 Direct3D 11.1 後處理。 |
| [延伸語言服務 (ELS) 範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示了擴展語言服務 (ELS) 在 Windows 應用商店應用中的使用。 該示例實現示範使用三個可用 ELS 服務的方案。 這些方案演示如何請求特定服務。 |
| [直接寫入測試範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用 DirectWrite 的命中測試功能。 它們用於確定正在按一下或觸控顯示的文本的哪一部分。 |
| [直接寫入內聯物件範例(Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例展示如何將內聯物件插入到文本佈局(如圖像)中。 |
| [基於 XAML 向量的繪圖範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何在應用中繪製基於向量的圖形。 |
| [藍牙呼叫控制範例(Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 藍牙呼叫控制示例展示如何配置預設藍牙通信設備以處理呼叫。 此示例有 JAVAScript、C#C++ 和VB.Net版本。 此示例需要瞭解 Windows 事件和事件處理。 |
| [Direct2D 指令列表示例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示了命令清單的使用。 它用於記錄一組向量命令,從命令列表中創建圖像畫筆,然後填充矩形幾何體。 命令清單保留向量的解析度獨立性。 |
| [控制通道觸發器 XMLHTTP請求範例(Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 該示例演示如何使用`ControlChannelTrigger`類 啟用 Windows 應用`IXMLHTTPRequest2`商店應用,使其始終連接且始終可訪問。 此示例演示了在 Windows 應用商店應用中使用後台網路通知。 |
| [X輸入與 JavaScript 控制器草圖範例(Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例展示如何在 Windows 執行時元件中包裝 XInput C++ API。 然後,它使用 JAVAScript 從 Windows 應用商店應用調用它。 此範例實現草圖應用,允許您使用 Xbox 遊戲控制器來選擇線粗等。 |
| [Direct2D 卷積矩陣效果範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示了 Direct2D 效果捲卷矩陣效果。 此示例有一些示例卷積內核矩陣:直通(無op)、框模糊(寬度 5)、簡單邊緣檢測、簡單銳化、浮雕、垂直塗抹(高度 10)等。 |
| [DirectX 交換鏈實現範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何接收`CoreWindow`本機應用程式中的事件,以及如何將 DirectX 交換鏈連接到應用程式檢視。 |
| [認證的取器範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用`Windows.Security.Credentials.UI.CredentialPicker`類 檢索憑據。 這些認證可能會傳遞給需要它們的 API,例如`HttpClient`。 |
| [Direct2D 動畫範例(Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用 Direct2D 沿螺旋路徑渲染 Direct2D 基元併為其設置動畫。 |
| [分享內容目標應用範例(Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何應用接收從其他應用共享的內容。 此範例使用和`Windows.ApplicationModel.DataTransfer``Windows.ApplicationModel.DataTransfer.Share`命名空間中的類。 |
| [直接2D儲存到影像檔案範例(Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用 Direct2D 和 DirectWrite 呈現到螢幕。 以及如何使用 WIC API 將渲染的圖像保存到磁碟。 |
| [根據 DPI 範例進行縮放(Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例介紹如何構建根據螢幕的圖元密度縮放的應用。 它載入適當比例的圖像或覆蓋預設縮放。 此示例使用`Windows.Graphics.Display`API。 |
| [建立 Windows 執行時行程內元件範例 (C#) (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例展示如何在 C# 中建立用於 C++/CX、JavaScript 和 C# 用戶端代碼的元件。 OvenServer 專案包含一個名為`Oven`的 運行時類,`IOven`它實現了一`IAppliance`個介面和一個介面。 |
| [推送及定期通知客戶端範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何用戶端應用註冊和偵聽從 Web 伺服器發送的推送通知。 推送通知可用於更新徽章或磁貼、引發 Toast 通知或啟動後台任務。 |
| [可攜式裝置 API 範例(Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此範例展示如何從C++應用存`IPortableDevice`取 COM API。 要瞭解如何從桌面C++應用`IPortableDevice`訪問 COM API,請參閱便攜式設備 COM API 範例。 |
| [PlayToReceiver 範例(Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何創建軟體"播放到接收器"。 要宣傳軟體"播放到接收器",請單擊"啟動接收器"按鈕。 要停止接收器,請按下「停止接收器」按鈕。 |
| [鎖定螢幕個人化範例(Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用`LockScreen`API 設置當前使用者的鎖屏映射。 此示例使用命名空間中的`Windows.System.UserProfile`類。 |
| [認證的儲物櫃範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用 WinRT `PasswordVault` API 以及如何使用認證儲物櫃記憶體 Web 認證。 特定方案包括具有單個資源的單個使用者和具有單個資源的多個使用者。 |
| [媒體引擎本機C++視頻播放範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示使用本機C++應用中的`MediaEngine`API 進行視頻播放。 |
| [媒體擴展示例(Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用媒體擴展。 您可以將效果應用於視頻、解碼視頻以及使用方案處理程式創建媒體流。 |
| [鎖定螢幕應用範例(Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例顯示應用如何在鎖屏介面上顯示,鎖定計算機時顯示的螢幕,帶有提供基本狀態資訊的鎖屏或磁貼以提供更詳細的狀態。 |
| [XAML 文字顯示範例(Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何控制應用中的文本外觀。 |
| [簡單定向感測器範例(Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用`Windows.Devices.Sensors.SimpleOrientationSensor`API。 |
| [Direct3D 精靈樣本(Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例提供子畫面批處理行為的 Direct3D 實現,類似於`SpriteBatch`XNA API。 Sprites 是二維位圖,可在三維場景中獨立轉換和管理,通常用於二維遊戲。 |
| [Direct3D 立體 3D 範例 (Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何使用 Direct3D 向C++應用添加立體三維效果。 它還演示了如何回應 Direct3D 中的系統立體聲更改。 立體三維效果需要支援立體三維的顯示幕。 |
| [使用C++範例建立 Windows 執行時 DLL 元件(Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例演示如何在 Microsoft Visual C++中創建進程內 DLL 元件。 它用於C++/CX、JavaScript 和 C# 客戶端代碼。 OvenServer 專案包含一個名為`Oven`的運行時類,該`IOven`類實現 介面。 |
| [使用C++範例建立 Windows 執行時 EXE 元件(Windows 8)](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) | 此示例展示如何在 Microsoft Visual C++中創建行程外 EXE 元件。 它用於C++/CX、JavaScript 和 C# 客戶端代碼。 OvenServer 專案包含一個名為`Oven`的運行時類,該`IOven`類實現 介面。 |
