---
---
>[!cards]
>**[[Rock of Bral]]**
>![[RockOfBral.jpg | sban hsmall p+t]]
>
>**[[0. Log| Session Log]]**
>![[CampaignJournal.png|sban hsmall ctr]]
>
>**[[1. The Party| The Party]]**
>![[PartyGeneric.avif|sban hsmall ctr]]

---
```dataviewjs
const calData = {  
	colors: {
		blue:        ["#8cb9ff", "#69a3ff", "#428bff", "#1872ff", "#0058e2"],
		green:       ["#c6e48b", "#7bc96f", "#49af5d", "#2e8840", "#196127"],
		red:         ["#ff9e82", "#ff7b55", "#ff4d1a", "#e73400", "#bd2a00"],
		orange:      ["#ffa244", "#fd7f00", "#dd6f00", "#bf6000", "#9b4e00"],
		pink:        ["#ff96cb", "#ff70b8", "#ff3a9d", "#ee0077", "#c30062"],
		orangeToRed: ["#ffdf04", "#ffbe04", "#ff9a03", "#ff6d02", "#ff2c01"]
	},
	entries: []
}

for(let page of dv.pages('"2. Sessions"').where(p => p.sessionDate))
{
	calData.entries.push({
		date: (new Date(page.sessionDate)).toISOString().slice(0,10),
		intensity: 1,
		content: await dv.span(`[[${page.file.name}|]]`) ,
		color: page.sessionstatus === "Occurred" ? "green" : "red"
	})
}

renderHeatmapCalendar(this.container, calData)
```
