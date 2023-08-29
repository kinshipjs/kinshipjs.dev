<script>
    import { Argument, ReturnType, Docs } from "$lib/components/syntax";

    const exampleCode = `import { KinshipContext } from "@Kinship/Kinship";
// initialize connection with desired adapter as \`connection\`.
const ctx: KinshipContext<Track> = new KinshipContext(connection, "Track"));`;

    const sqlCode = `SELECT * ...`
</script>

<h2 class="h2">new KinshipContext()</h2>
<div class="p-4">
    <Docs {exampleCode}>
        Construct a new <code class="code">KinshipContext</code> class object for usage of interacting with a singular table in your database.
        <svelte:fragment slot="note">
            To achieve the most of this library, you must explicitly pass in a parameter type into <code class="code">KinshipContext</code>.
            <br>
            <small class="italic">You ONLY need the first parameter type, <code class="code">TTableModel</code></small>
        </svelte:fragment>
        <svelte:fragment slot="parameters">
            <Argument name="adapter" type="MyORMAdapter">
                Adapter used to connect to your database.
            </Argument>
            <Argument name="realTableName" type="string">
                Name of the table you are connecting to.
            </Argument>
        </svelte:fragment>
        <svelte:fragment slot="returns">
            <ReturnType type="KinshipContext">
                Class object to interact with your table.
            </ReturnType>
        </svelte:fragment>
    </Docs>
</div>
