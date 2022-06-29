<script>
    export let temtem;
</script>

<div class="border-2 border-slate-700 rounded-md">
    <div class="flex justify-between overflow-hidden border-b-2 border-slate-700">
        <span class="font-medium w-auto h-auto ml-2">#{temtem.number}</span>
        <h2 class="font-medium mr-2">{temtem.name}</h2>
    </div>
    <div class="overflow-hidden">
        <img class="transition-all hover:scale-105" src="{temtem.wikiPortraitUrlLarge}" alt="{temtem.name} image"/>
    </div>
</div>
