<script>
    import Wallet from '$lib/Wallet.svelte';

    let wallets = $state([])

    let data = $state({
        name: '',
        amount: 0
    })

    function submit() {
        const obj = {
            id: wallets.length + 1,
            name: data.name,
            amount: data.amount,
            date: (new Date()).getDate()
        }
wallets = [...wallets, obj]
data.name = ""
data.amount = 0
    }
</script>

<h1 class="text-3xl uppercase text-center font-semibold mb-10">
    expense tracker
</h1>

<div class="space-y-3">
    <h1 class="text-2xl">Add new wallet</h1>
    <div>
        <span class="block mb-1 capitalize">name</span>
        <input
bind:value={data.name}
            type="text"
            name="name"
            class="w-full border py-1 rounded-lg px-2"
        />
    </div>
    <div>
        <span class="block mb-1">Amount</span>
        <input
bind:value={data.amount}
            type="tel"
            name="name"
            class="w-full border py-1 rounded-lg px-2"
        />
    </div>
    <button
    disabled={data.name == "" || data.amount == ""}
    onclick={submit}
        class="border w-full p-2.5 text-sm rounded-lg bg-black text-white hover:bg-white hover:text-black transition-colors"
        >Add Wallet</button
    >
</div>

<h1 class="mt-5 mb-2 font-semibold">Wallets</h1>

<div class="space-y-3">
    {#each wallets as wallet}
    <Wallet name={wallet.name} amount={wallet.amount} date={wallet.date} />
    {/each}
</div>
