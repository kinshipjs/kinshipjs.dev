<script>
    import { Argument, ReturnType, Docs } from "$lib/components/syntax";

    const exampleCode = `import { KinshipContext } from "@Kinship/Kinship";
// initialize connection with desired adapter as \`connection\`.
const ctx: KinshipContext<Track> = new KinshipContext(connection, "Track"));
ctx.sortBy(m => m.Composer.desc())
    .select();`;

    const sqlCode = ``;
</script>

<h2 class="h2">.desc()</h2>
<div class="p-4">
    <Docs {exampleCode} {sqlCode} synonyms={["descending"]}>
        Specifies the direction of a property being sorted on to be in <code class="code">DESCENDING</code> order.
        <svelte:fragment slot="returns">
            <ReturnType type="KinshipContext">
                A new <code class="code">KinshipContext</code> class object with the same state as the original <code class="code">KinshipContext</code> and with the added state of the clause specified.
            </ReturnType>
        </svelte:fragment>
    </Docs>
</div>
