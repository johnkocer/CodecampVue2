<template>
  <div id="app">
    <h3>MyInheritance</h3>
    {{this.inheritance()}}
  </div>
</template>

<script>
/* eslint-disable */

export default {
  name: "MyInheritance",

  methods: {
    inheritance() {
      class IMember {
        id;
        name;
      }

      let member = { id: 1, name: "James" };
      console.log(member);

      class ClubMember extends IMember {
        id;
        name;
        memberFee;
      }

      class GoldMember extends ClubMember {
        goldMemberFee;
      }

      let goldMember = new GoldMember();
      goldMember.id = 1;
      goldMember.goldMemberFee = 20;
      console.log(`id: ${goldMember.id} Fee: ${goldMember.goldMemberFee} `);
      // id: 1 Fee: 20
    }
  }
};
</script>