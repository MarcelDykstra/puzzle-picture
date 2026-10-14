[![EMERGENCY SITUATION !!](https://img.shields.io/badge/EMERGENCY%20SITUATION%20!!-red?style=for-the-badge)](https://www.youtube.com/watch?v=3sHrKeqIlt8)

# Puzzle Picture — [ROOT framework (CERN)](https://root.cern/) — Record CVEs, Zero-Days & Exploits

[![Puzzle Picture — ROOT](puzzle-picture-ROOT.png)](https://www.auger.org/)

```C++
#include <vector>
#include <ranges>
#include <TStyle.h>
#include <TArrayI.h>
#include <TColor.h>
#include <TH2F.h>
#include <TCanvas.h>
#include <TScatter.h>

int main()
{
    const auto nBins = 20;  // Limit number of color-bins, independent of numbered-ticks in colorbar.

    gStyle->SetPalette(kRainBow);
    const TArrayI& palette = TColor::GetPalette();
    const auto palSize = palette.GetSize();
    auto binPaletteView = std::views::iota(0, nBins)
                          | std::views::transform([&](int idx) {
                                return palette[idx * (palSize / nBins)];
                            });  // ROOT 6 greatly increased number of colors in palettes.

    std::vector<int> binPalette(binPaletteView.begin(), binPaletteView.end());
    gStyle->SetPalette(nBins, binPalette.data(), 1);

    std::vector<double> x = {0, 0, -160, 160, -160,  160,   0,    0, 320, -320, 240,  240, -240, -240};
    std::vector<double> y = {0, 0,  280, 280, -280, -280, 280, -280,   0,    0, 140, -140,  140, -140};
    std::vector<double> c = {0, 4,   10,   2, 17.5,    6,  12,    7,  16,    2,  15,    8,   16,    9};
    auto [cMin, cMax] = std::ranges::minmax(c);

    auto canvas = std::unique_ptr<TCanvas>(new TCanvas("c1", "scatter plot", 800, 600));
    auto scatter = std::unique_ptr<TScatter>(new TScatter(x.size(), x.data(), y.data(), c.data(), nullptr));

    scatter->SetMarkerStyle(21);
    scatter->SetMarkerSize(0.7);
    scatter->GetHistogram()->SetMinimum(cMin);
    scatter->GetHistogram()->SetMaximum(cMax);

    scatter->GetHistogram()->SetTitle("hexagonal grid (...). mean ... time; x [m]; y [m]");
    gStyle->SetTitleBorderSize(1);  // Add a personal touch, with border around title.
    gStyle->SetTitleFontSize(0.035);

    scatter->Draw("AP");
    canvas->SaveAs("puzzle-picture-ROOT.png");

    return 0;
}
```

> Kant's Axe? (No background in grammar?): "_[Alleen **zij** die groots **durven** te falen, **kunnen** ooit groots bereiken.](https://citaten.net/quotes/robert_f_kennedy/40114/citaat-alleen-wie-het-aandurft-om-groots-te-falen-krijgt-de-kans-om.html)_" — Robert F. Kennedy

[References](REFERENCES.md)

[![puzzle-picture-ROOT — License](https://img.shields.io/badge/LICENSE-MIT-blue?style=for-the-badge)](LICENSE.md)
[![ROOT — License](https://img.shields.io/badge/LICENSE-ROOT%20(GNU%20LGPL)-blue?style=for-the-badge)](https://root.cern/about/license/)
[![FOSDEM 2026](https://img.shields.io/badge/FOSDEM%202026-red?style=for-the-badge)](https://archive.fosdem.org/2026/schedule/event/FE7ULY-foss-in-times-of-war-scarcity-and-ai/)
[![xkcd 2347](https://img.shields.io/badge/xkcd%202347-red?style=for-the-badge)](https://xkcd.com/2347/)
[![XZ backdoor](https://img.shields.io/badge/XZ%20backdoor-red?style=for-the-badge)](https://en.wikipedia.org/wiki/XZ_Utils_backdoor)
[![FOSDEM 2026](https://img.shields.io/badge/FOSDEM%202026-red?style=for-the-badge)](https://archive.fosdem.org/2026/schedule/event/L3BK7S-free-as-in-burned-out/)
[![FOSDEM 2026](https://img.shields.io/badge/FOSDEM%202026-red?style=for-the-badge)](https://archive.fosdem.org/2026/schedule/event/MYSK9E-openness-of-oss-communities/)
[![FOSDEM 2026](https://img.shields.io/badge/FOSDEM%202026-red?style=for-the-badge)](https://archive.fosdem.org/2026/schedule/event/XWSW3R-the_geopolitics_of_open_source_software/)
[![Code Quality ?](https://img.shields.io/badge/Code%20Quality%20%3F%20—%20Vulnerability%20Model%20Autophagy%20Disorder%20v(MAD)-red?style=for-the-badge)](https://innovationgraph.github.com/global-metrics/git-pushes)
[![NASDAQ !!!](https://img.shields.io/badge/NASDAQ%20!!!-red?style=for-the-badge)](https://nl.wikipedia.org/wiki/Beurskrach_van_1929)
[![Pandora's Box !?!!](https://img.shields.io/badge/Pandora's%20Box%20!%3F!!-red?style=for-the-badge)](https://www.sciencefocus.com/news/internet-collapse-mythos-ai)
[![CVE Statistics 2025 !!!](https://img.shields.io/badge/CVE%20Statistics%202025%20—%20Backdoors%20—%20Low%20Hanging%20Fruits%20!!!-orange?style=for-the-badge)](https://deepstrike.io/blog/vulnerability-statistics-2025)
[![LLM Sock Puppetry !?!? ;)](https://img.shields.io/badge/LLM%20Sock%20Puppetry%20!%3F!%3F%20;\)-red?style=for-the-badge)](https://lwn.net/Articles/1087162/)
[![AUR Incident !!](https://img.shields.io/badge/AUR%20Incident%20!!-blue?style=for-the-badge)](https://archlinux.org/news/active-aur-malicious-packages-incident/)
[![ARPANET !](https://img.shields.io/badge/ARPANET%20(DoD)%20!-green?style=for-the-badge)](https://en.wikipedia.org/wiki/ARPANET)
[![Cisco !!!](https://img.shields.io/badge/Cisco%20!!!-green?style=for-the-badge)](https://www.cisco.com/site/us/en/solutions/artificial-intelligence/cisco-defending-against-ai-attacks-guidance.html)
[![Mythos !](https://img.shields.io/badge/Mythos%20—%20Critical%20Patches%20—%20Thanks%20Bro%20!-green?style=for-the-badge)](https://mythoscvetracker.com)
[![Glasswing !!!](https://img.shields.io/badge/Glasswing%20—%20Critical%20Patches%20—%20Thanks%20Bros%20!!!-green?style=for-the-badge)](https://www.anthropic.com/glasswing)
[![Guardrails !](https://img.shields.io/badge/Gaurdrails%20—%20Logical%20Reasoning%20(Profit%20%3F)%20!-green?style=for-the-badge)](https://blog.equinix.com/blog/2026/08/04/what-is-a-network-in-the-ai-era-the-answer-is-changing/)
[![Linus Torvalds !!!](https://img.shields.io/badge/Linus%20Torvalds%20—%20"we%20don't%20break%20user%20space"%20!!!-green?style=for-the-badge)](https://lwn.net/Articles/416821/)
[![Emergency Situation 11-2025 !!](https://img.shields.io/badge/Emergency%20Situtatuation%2011--2025%20!!-green?style=for-the-badge)](https://www.rijksoverheid.nl/actueel/nieuws/2025/11/03/overheid-start-campagne-denk-vooruit-voorbereiden-op-noodsituatie-steeds-belangrijker)
[![Emergency Situation 11-2025 !!](https://img.shields.io/badge/Emergency%20Situation%2011--2025%20!!-green?style=for-the-badge)](https://www.rijksoverheid.nl/actueel/nieuws/2025/11/17/minister-van-oosten-presenteert-informatieboekje-bereid-je-voor-op-een-noodsituatie)
[![Emergency Situation 10-2026 !!](https://img.shields.io/badge/Emergency%20Situatuation%2010--2026%20!!-green?style=for-the-badge)](https://www.rijksoverheid.nl/actueel/nieuws/2026/10/12/nieuwe-denk-vooruit-campagne-om-extra-aandacht-te-vragen-om-voor-te-bereiden-op-noodsituatie)
