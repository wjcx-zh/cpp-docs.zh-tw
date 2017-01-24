---
title: "起始頁最佳做法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "起始頁秘訣"
  - "起始頁最佳做法"
  - "起始頁設計"
ms.assetid: f6ce1ce0-746e-4004-a37f-6f176f6f5851
caps.latest.revision: 16
caps.handback.revision: 16
manager: "douge"
---
# 起始頁最佳做法
由於起始頁可以存取 Visual Studio 命令，並且會在每次載入 Visual Studio 時開啟，因此建議您在使用或散發任何自訂起始頁之前，先確保其穩定無虞。 本主題建議強大起始頁設計的最佳做法，並包含有關如何建立實用使用者介面 \(UI\) 的指導方針。  
  
## 穩定性指導方針  
  
### 資源可用性  
 建立強大自訂起始頁的最重要考量是確保所有必要資源皆可供使用：  
  
-   已安裝所有必要封裝。  
  
-   已預先載入封裝。  
  
-   所有必要組件皆位於 \\PrivateAssemblies\\ 資料夾中。  
  
-   每個使用網路或網際網路連線的元件皆有因應離線情況和中斷連線的替代方案。  
  
### 效能  
 如果您的起始頁具有大量記憶體需求或載入許多資源，請考慮啟動效能所受到的影響。 將這類起始頁編寫成只有在需要時才載入元件，或在可行時於背景執行，讓啟動時間不會大幅增加。  
  
### 開發程序  
 直接修改使用中的起始頁可能會不小心引入錯誤，從而造成 Visual studio 損毀。 因為每次開啟 Visual Studio 就會開啟起始頁，所以很難修正損毀的起始頁。 因此，建議您修改起始頁檔案的複本，並在 Visual Studio 的實驗執行個體中測試其可靠性。 當新的起始頁穩定時，您便可以藉由設定而使該起始頁在 Visual Studio 的主要執行個體中執行。  
  
> [!NOTE]
>  此外也建議您在 Visual Studio 的實驗執行個體中測試任何協力廠商起始頁，再用於主要執行個體中。  
  
##### 在 Visual Studio 的實驗執行個體中測試起始頁  
  
1.  如果使用起始頁專案範本，請按 F5 鍵。 否則就是：  
  
    1.  將您的 .xaml 檔以及支援的文字或標記複製到 \\%USERPROFILE%\\My Documents\\Visual Studio *\<版本\>*\\StartPages\\ 中。  
  
    2.  將任何必要組件複製到 *\<Visual Studio 安裝路徑\>*\\Common7\\IDE\\PrivateAssemblies\\ 中。  
  
    3.  在 Visual Studio 命令提示字元中，使用下列命令來開啟 Visual Studio 的實驗執行個體。  
  
         **Devenv \/rootsuffix exp**  
  
2.  在 \[**工具**\] 功能表上按一下 \[**選項**\]。 展開 \[環境\]，然後選取 \[啟動\]。 在 \[自訂起始頁\] 清單中，選取已重新命名的 StartPage.xaml 檔案，然後按一下 \[確定\]。  
  
3.  從 \[檢視\] 功能表按一下 \[起始頁\]。  
  
     自訂起始頁隨即開啟。 如果您要修改的起始頁損毀，您可以重新啟動 Visual Studio 的主要執行個體、進行必要的修正，然後開啟另一個實驗執行個體以便您可以繼續修改自訂起始頁。  
  
 如果您的起始頁損毀 Visual Studio 的主要執行個體，您可以將 HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\14.0\\StartPage\\Default\\CustomizationEnabled 的登錄值設定為 0，來暫時停用自訂起始頁。 或者，您可以將目前預設起始頁的 .xaml 檔暫時重新命名。 上述任一方法都可讓您開啟 Visual Studio 一段足夠的時間來修正錯誤。  
  
### 偵錯  
 \[起始頁\] 工具視窗會在第一次載入起始頁時攔截例外狀況，但之後不會攔截例外狀況。 您可以將下列登錄值設定為 "1"，指示 Visual Studio 顯示所有未處理的例外狀況。  
  
 HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\14.0\\General\\EnableUnhandledExceptionDisplay  
  
 例外狀況資訊會顯示在訊息方塊中，讓您偵錯起始頁上或其他未處理位置中的控制項，甚至是主要 Visual Studio 執行個體中的位置。 如果引發例外狀況之後無法偵錯，您可以使用 "devenv \/safemode" 命令重新啟動 Visual Studio、切換回上一個起始頁，然後繼續在實驗執行個體中進行偵錯。  
  
### 相對路徑  
 當您參考起始頁中的檔案路徑時，請一律使用相對路徑，以允許不同的系統設定。 不過，起始頁上所有相對路徑的根目錄不會解析至 \\StartPages\\ 資料夾，而是解析至 ..\\*Visual Studio 安裝資料夾*\\Common7\\IDE，也就是 devenv.exe 所在位置。 若要將路徑設定為相對於 \\StartPages\\ 資料夾，請使用 VS 啟始頁相對轉換器。 方法是將物件的 `Source` 屬性設定為 `vs:StartPageRelative`，如下列範例所示。  
  
 XAML  
  
```  
<Image Source="{vs:StartPageRelative myImage.png}" .../>  
```  
  
 存取 Visual Studio 隨附的資源或包含在其他封裝中的檔案時，請使用標準相對路徑語法。  
  
### 部署  
 建議您採用下列最佳做法，將自訂起始頁部署到其他使用者。  
  
#### 使用者設定  
  
-   採用使用者設定。 不要覆寫現有的起始頁喜好設定。  
  
#### VSIX  
 這些做法適用於 VSIX 部署：  
  
-   使用 VSIX 資訊清單中的 [GettingStartedGuide](http://msdn.microsoft.com/zh-tw/261bb1fd-abae-4ed6-80a8-90d5fc3bb8c6) 項目，指向如何設定預設起始頁的相關指示。  
  
-   使用 VSIX 資訊清單的 [Name](http://msdn.microsoft.com/zh-tw/d99d38d1-060b-401a-9b9f-ede2c6213a11) 項目和 [Description](http://msdn.microsoft.com/zh-tw/24ddc57e-e991-4a43-b0c9-0e76da293e99) 項目，清楚地識別作為起始頁的擴充功能，並說明其目的。  
  
-   確認您的 VSIX 資訊清單未包含絕對路徑。  
  
-   當您上傳至 [Visual Studio 組件庫](http://go.microsoft.com/fwlink/?LinkID=123847)網站時，請包含相關的標記，讓使用者可以識別作為起始頁的擴充功能。  
  
#### MSI  
 如果您要將起始頁當做在 Windows Installer \(MSI\) 封裝中部署之更大型擴充功能的一部分來產生，您可以設定起始頁安裝成目標電腦上的預設起始頁。 若要完成這個工作，請將起始頁 .xaml 檔的名稱寫入下列登錄機碼的 URI 值：HKCU\\Software\\Microsoft\\VisualStudio\\14.0\\StartPage\\Default\\。 請採用下列指導方針來設定這個登錄值：  
  
-   在安裝程式中提供 UI，讓使用者可以選擇是否要將新的起始頁設為預設值。  
  
-   如果使用者解除安裝您的擴充功能，請還原先前的登錄值。  
  
### Windows Presentation Framework \(WPF\)  
 您的 XAML 標記應該遵循 WPF 最佳做法。 如需 [!INCLUDE[TLA#tla_winclient](../misc/includes/tlasharptla_winclient_md.md)] 和 [!INCLUDE[TLA#tla_netframewk](../misc/includes/tlasharptla_netframewk_md.md)] 應用程式開發最佳做法的相關資訊，請視需要參閱下列主題。  
  
|區域|主題|  
|--------|--------|  
|協助工具選項|[Accessibility Best Practices](../Topic/Accessibility%20Best%20Practices.md)|  
|當地語系化|[WPF 全球化和當地語系化概觀](../Topic/WPF%20Globalization%20and%20Localization%20Overview.md)|  
|效能|[最佳化 WPF 應用程式效能](../Topic/Optimizing%20WPF%20Application%20Performance.md)|  
|安全性|[安全性 \(WPF\)](../Topic/Security%20\(WPF\).md)|  
  
## 使用者介面指導方針  
 為了確保起始頁有方便且簡單易懂的使用者體驗，請在適用的情況下採用下列 UI 指導方針。  
  
### 上方資料列  
  
#### 橫幅  
  
-   將橫幅影像高度設為包含影像之資料列的資料列定義高度。  
  
-   為了配合不同的視窗大小和螢幕解析度，請將橫幅影像設為賞心悅目的任何寬度。  
  
-   保持橫幅區域的整齊。 標誌與其他按鈕或圖形不得重疊。  
  
### 左欄  
  
#### 按鈕區域  
  
-   僅在按鈕區域中放置最常使用的控制項，以挪出空間顯示最近使用的專案名稱。 建議放置五個以下的按鈕。  
  
#### 最近使用的專案  
  
-   這個控制項可讓使用者存取最近使用的專案。 您可以將要顯示的專案數目設定為 0 到 24。 由於這是起始頁最常使用的區段，因此建議您不要移除此區段。  
  
#### 起始頁選項  
  
-   請確定在起始頁上顯示 \[專案載入後關閉頁面\] 和 \[啟動時顯示頁面\] 選項。  
  
-   如果這個區域還需要其他控制項，建議您使用核取方塊或選項按鈕，並確定這些控制項與起始頁喜好設定相關。  
  
### 內容區域  
  
#### 最上層索引標籤  
  
-   避免加入過多的索引標籤，使得索引標籤控制項在一般螢幕寬度下換行。  
  
-   使用簡短、描述性的索引標籤名稱。  
  
-   確定索引標籤代表群組的內容區域。  
  
#### 子層級索引標籤  
  
-   只有在您有兩個以上的子主題時才使用子層級導覽。  
  
-   避免加入過多的索引標籤，使得索引標籤控制項在一般螢幕寬度下換行。  
  
-   使用簡短、描述性的索引標籤名稱。  
  
#### 子層級索引標籤內容  
  
-   子層級索引標籤上顯示的內容項目不得超過五個。  
  
#### 項目內容  
  
-   每個內容項目顯示的連結不得超過四個。  
  
-   如果您將影像與內容項目建立關聯，請確定每個影像的大小為 175x125 像素。  
  
-   使用簡短、描述性的內容項目標題。  
  
-   將內容項目的描述限制為兩句或更少。  
  
### 一般  
  
#### Animations  
  
-   如果使用動畫，將其限制為 0.5 秒 \(含\) 以下可避免有效能不佳的感覺。  
  
#### 環境色彩  
  
-   字型和色彩採用系統設定。  
  
-   使用淺色背景。  
  
-   使用遠端桌面偵測，以確保遠端工作階段中的色彩適當調降。  
  
## 請參閱  
 [起始頁架構](../misc/start-page-architecture.md)   
 [部署自訂起始頁](../Topic/Deploying%20Custom%20Start%20Pages.md)   
 [將 Visual Studio 命令加入至 \[開始\] 頁面](../Topic/Adding%20Visual%20Studio%20Commands%20to%20a%20Start%20Page.md)