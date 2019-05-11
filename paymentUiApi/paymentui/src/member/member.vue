<template>
  <fieldset>
    <legend>
      <span style="isMemberSuccess">Customer Info:</span>
    </legend>
    <div ng-style="isMemberSuccess" class="col col-sm">
      <div c>
        <label>Member ID:</label>
        <span>{{ member.id }}</span>
      </div>
      <div>
        <label>Name:</label>
        <span>{{ member.fullName }}</span>
      </div>
      <div>
        <label class="memberTH">Zip Code:</label>
        <span>{{ member.zipCode }}</span>
      </div>
    </div>
  </fieldset>
</template>

<script>
/* eslint-disable */
import { PaymentService } from "../service/payment.service";
import { Member } from "../service/app.classLibrary";

export default {
  name: "MemberComponent",
  props: {},
  data() {
    return {
      member: Member
    };
  },
  mounted() {
    console.log("in Mounted");
    this.getMember();
  },
  methods: {
    getMember() {
      PaymentService.getMember(1)
        .then(res => {
          this.member = res.data;
          this.triggerMemberEvent();
        })
        .catch(error => {
          console.log("There is an error in getMember API call." + error);
        });
    },
     triggerMemberEvent() {
      console.log("In triggreEvent", this.member);
      this.$root.$emit("emitFromMember", this.member);
    }
  } // methods
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->