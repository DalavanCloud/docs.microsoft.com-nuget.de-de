1. <span data-ttu-id="a177e-101">[Melden Sie sich bei Ihrem nuget.org-Konto an](https://www.nuget.org/users/account/LogOn?returnUrl=%2F), oder erstellen Sie ein Konto, wenn Sie noch keines besitzen.</span><span class="sxs-lookup"><span data-stu-id="a177e-101">[Sign into your nuget.org account](https://www.nuget.org/users/account/LogOn?returnUrl=%2F) or create an account if you don't have one already.</span></span>

1. <span data-ttu-id="a177e-102">Klicken Sie auf Ihren Benutzernamen (oben rechts) und anschließend auf **API Keys** (API-Schlüssel).</span><span class="sxs-lookup"><span data-stu-id="a177e-102">Select your user name (on the upper right), then select **API Keys**.</span></span>

1. <span data-ttu-id="a177e-103">Wählen Sie **Erstellen**, geben Sie einen Namen für den Schlüssel ein, und wählen Sie **Bereiche auswählen > Push**.</span><span class="sxs-lookup"><span data-stu-id="a177e-103">Select **Create**, provide a name for your key, select **Select Scopes > Push**.</span></span> <span data-ttu-id="a177e-104">Geben Sie unter **API-Schlüssel** für **Globmuster** ein Sternchen (\*) ein, und wählen Sie dann **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="a177e-104">Under **API Key**, enter \* for **Glob pattern**, then select **Create**.</span></span> <span data-ttu-id="a177e-105">(Weitere Informationen zu Bereichen finden Sie unten.)</span><span class="sxs-lookup"><span data-stu-id="a177e-105">(See below for more about scopes.)</span></span>

1. <span data-ttu-id="a177e-106">Nachdem der Schlüssel erstellt wurde, klicken Sie auf **Copy** (Kopieren), um den Zugriffsschlüssel abzurufen, den Sie in der CLI benötigen:</span><span class="sxs-lookup"><span data-stu-id="a177e-106">Once the key is created, select **Copy** to retrieve the access key you need in the CLI:</span></span>

    ![Kopieren des API-Schlüssels in die Zwischenablage](../media/QS_Create-02-APIKey.png)

1. <span data-ttu-id="a177e-108">**Wichtig**: Speichern Sie Ihren Schlüssel an einem sicheren Ort, Sie können den Schlüssel später nicht erneut kopieren.</span><span class="sxs-lookup"><span data-stu-id="a177e-108">**Important**: Save your key in a secure location because you cannot copy the key again later on.</span></span> <span data-ttu-id="a177e-109">Wenn Sie auf die Seite „API-Schlüssel“ zurückkehren, müssen Sie den Schlüssel erneut generieren, um ihn zu kopieren.</span><span class="sxs-lookup"><span data-stu-id="a177e-109">If you return to the API key page, you need to regenerate the key to copy it.</span></span> <span data-ttu-id="a177e-110">Sie können den API-Schlüssel auch entfernen, wenn sie keine Pakete mehr mithilfe von Push über die CLI übertragen möchten.</span><span class="sxs-lookup"><span data-stu-id="a177e-110">You can also remove the API key if you no longer want to push packages via the CLI.</span></span>

<span data-ttu-id="a177e-111">Mit der Bereichsauswahl können Sie separate API-Schlüssel für verschiedene Zwecke erstellen.</span><span class="sxs-lookup"><span data-stu-id="a177e-111">Scoping allows you to create separate API keys for different purposes.</span></span> <span data-ttu-id="a177e-112">Jeder Schlüssel hat seinen Ablaufzeitraum und kann auf bestimmte Pakete (oder Globmuster) festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="a177e-112">Each key has its expiration timeframe and can be scoped to specific packages (or glob patterns).</span></span> <span data-ttu-id="a177e-113">Jeder Schlüssel ist zudem auf bestimmte Vorgänge begrenzt: Push von neuen Paketen und Updates, Push von ausschließlich Updates oder Entfernen aus Listing.</span><span class="sxs-lookup"><span data-stu-id="a177e-113">Each key is also scoped to specific operations: push of new packages and updates, push of updates only, or delisting.</span></span> <span data-ttu-id="a177e-114">Durch das Festlegen des Gültigkeitsbereichs können Sie API-Schlüssel für verschiedene Personen erstellen, die Pakete für Ihre Organisation so verwalten, dass sie nur über die erforderlichen Berechtigungen verfügen.</span><span class="sxs-lookup"><span data-stu-id="a177e-114">Through scoping, you can create API keys for different people who manage packages for your organization such that they have only the permissions they need.</span></span> <span data-ttu-id="a177e-115">Weitere Informationen finden Sie in der [Einführung in API-Schlüssel mit begrenztem Gültigkeitsbereich](https://blog.nuget.org/20170202/introducing-scoped-api-keys.html) (blogs.nuget.org).</span><span class="sxs-lookup"><span data-stu-id="a177e-115">For more information, see [Introducing scoped API keys](https://blog.nuget.org/20170202/introducing-scoped-api-keys.html) (blogs.nuget.org).</span></span>