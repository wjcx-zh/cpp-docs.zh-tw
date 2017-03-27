---
layout: LandingPage
title: "Visual C++ 中的資料存取"
translationtype: Human Translation
ms.sourcegitcommit: f9e63f47a8df69b52a6a12688e84602981d20dae
ms.openlocfilehash: 807cf772d632f66f74a210985ff611fc31ee594a
ms.lasthandoff: 03/21/2017

---
# <a name="data-access-in-visual-c"></a>Visual C++ 中的資料存取

幾乎所有 SQL 和 NoSQL 資料庫產品都會提供原生 C++ 應用程式的介面。 此業界標準介面是 ODBC，所有主要的 SQL 資料庫產品和許多 NoSQL 產品均提供相關支援。 對於非 Microsoft 產品，請洽詢廠商以取得詳細資訊。 此外，還有具各種授權條款的協力廠商程式庫可供使用。

從 2011 年開始，Microsoft 已經過調整，並以 ODBC 作為原生應用程式連線到內部部署和雲端 Microsoft SQL Server 資料庫的標準。 如需詳細資訊，請參閱[資料存取程式設計 \(MFC-ATL\)](data-access-programming-mfc-atl.md)。 C++/CLI 程式庫可以使用原生 ODBC 驅動程式或 ADO.NET。 如需詳細資訊，請參閱[使用 ADO.NET 進行資料存取 (C++/CLI)](/dotnet/data-access-using-adonet-cpp-cli.md) 和[存取 Visual Studio 中的資料](https://docs.microsoft.com/visualstudio/data-tools/accessing-data-in-visual-studio)。

<ul class="panelContent cardsF">
<li>
        <a href="/azure/sql-database/sql-database-develop-cplusplus-simple">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="/azure/media/index/SQLDatabase.svg" alt="" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>使用 C 和 C++ 連線到 SQL Database</h3>
                        <p>從 C 或 C++ 應用程式連線到 Azure SQL Database</p>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
    <li>
        <a href="https://github.com/Azure/azure-storage-cpp">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="/azure/media/index/Storage.svg" alt="" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>C++ 的 Microsoft Azure 儲存體用戶端程式庫</h3>
                        <p>[Azure 儲存體](/azure/storage/storage-introduction)是新式應用程式的雲端儲存解決方案，這些應用程式依賴持久性、可用性和延展性來符合客戶的需求。 使用 C++ 的 Azure 儲存體用戶端程式庫，從 C++ 連線到 Azure 儲存體。</p>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
    <li>
        <a href="https://blogs.msdn.microsoft.com/sqlnativeclient/2016/08/01/announcing-the-odbc-driver-13-1-for-sql-server/">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="/media/common/i_drivers.svg" alt="" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>ODBC Driver 13.1 for SQL Server - Windows 發行</h3>
                        <p>此最新的 ODBC 驅動程式為 C/C++ 架構應用程式，提供對 Microsoft SQL Server 2016 和 Microsoft Azure SQL Database 的強固資料存取。 其所支援的功能包括 Always Encrypted、Azure Active Directory 和 AlwaysOn 可用性群組。 也適用於 MacOS 及 Linux。</p>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
    <li>
        <a href="https://msdn.microsoft.com/library/ms130892.aspx">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="/media/common/i_api.svg" alt="" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>SQL Server Native Client</h3>
                        <p>SQL Server Native Client 是支援 SQL Server 2005 到 SQL Server 2014 的獨立資料存取應用程式開發介面 (API)，可用於 OLE DB 和 ODBC。 新的應用程式應該使用 ODBC Driver 13.1 for SQL Server。</p>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
    <li>
        <a href="/cpp/data/data-access-programming-mfc-atl">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="/media/common/i_api.svg" alt="" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>資料存取程式設計</h3>
                        <p>說明使用 Visual C++ 的舊版資料存取設計程式，慣用方法為使用其中一個類別庫，例如 Active Template Class Library (ATL) 或 Microsoft Foundation Class (MFC) 程式庫，這可以簡化使用資料庫 API。</p>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
    <li>
        <a href="/cpp/data/odbc/open-database-connectivity-odbc">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="/media/common/i_multi-connect.svg" alt="" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>開放式資料庫連接 (ODBC)</h3>
                        <p>Microsoft Foundation Classes (MFC) 程式庫提供可以使用開放式資料庫連接 (ODBC) 進行程式設計的類別。</p>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
    <li>
        <a href="/cpp/data/oledb/ole-db-programming">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="/media/common/i_generic-database.svg" alt="" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>OLE DB 程式設計</h3>
                        <p>提供討論 OLE DB 資料庫技術和 OLE DB 範本庫的概念性主題連結。 (除了與連結伺服器有關的案例之外，不建議新的應用程式使用 OLE DB)。</p>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
    
</ul>

---

<h2>參考資料</h2>

<ul class="panelContent cardsW">
 <li>
        <a href="https://azure.microsoft.com/develop/cpp/">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardText">
                        <h3>Microsoft Azure C 和 C++ 開發人員中心</h3>
                        <p>Azure 可讓您使用最愛的工具，以更具有彈性、延展性及可靠的方式，輕鬆建置 C++ 應用程式。</p>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
    <li>
        <a href="https://docs.microsoft.com/azure/storage/storage-c-plus-plus-how-to-use-blobs">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardText">
                        <h3>如何使用 C++ 的 Blob 儲存體</h3>
                        <p>Azure Blob 儲存體是可將非結構化的資料儲存在雲端作為物件/Blob 的服務。 Blob 儲存體可以儲存任何類型的文字或二進位資料，例如文件、媒體檔案或應用程式安裝程式。 Blob 儲存體也稱為物件儲存體。</p>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
    <li>
        <a href="https://docs.microsoft.com/sql/odbc/reference/odbc-programmer-s-reference">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardText">
                        <h3>ODBC 程式設計人員參考</h3>
                        <p>ODBC 介面是專為搭配 C 程式設計語言使用所設計。 ODBC 介面可用於下列三方面︰SQL 陳述式、ODBC 函式呼叫和 C 程式設計。</p>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
    <li>
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardText">
                        <h3><a href="https://www.microsoft.com/download/details.aspx?id=53339" title="Microsoft® ODBC Driver 13.1 for SQL Server® - Windows Download Page">ODBC Driver 13.1 for SQL Server</a></h3>
                        <p>Microsoft ODBC Driver 13.1 for SQL Server 是單一的動態連結程式庫 (DLL)，可為使用機器碼 API 連線到 Microsoft SQL Server 2008、SQL Server 2008 R2、SQL Server 2012、SQL Server 2016、分析平台系統、Azure SQL Database 及 Azure SQL 資料倉儲的應用程式提供執行階段支援。 您 可以前往這裡下載此驅動程式。</p>
                    </div>
                </div>
            </div>
        </div>        
    </li>
    
</ul>
