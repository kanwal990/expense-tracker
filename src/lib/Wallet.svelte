<script>
    let {name, amount, date} = $props();
</script>

<div class="border rounded-lg px-2 border-l-4 border-black">
    <div class="flex justify-between mb-1">
        <span>{name}</span>
        <span>{amount}</span>
    </div>
    <div class="flex justify-between mb-1">
        <span class="text-sm text-gray-500">{date}</span>
        <span>{'->'}</span>
    </div>
</div>