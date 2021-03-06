<template>
	<div class="selling">
		<top-info textHtml="Selling is our specialty." img="https://www.melbournerealestate.com.au/wp-content/uploads/2014/05/Sell_Hero.jpg"></top-info>
		<el-row class="content">
			<el-col class="content-desc" :md="24" :lg="17">
				<el-card class="content-desc-inner">
					<strong>Sell with MRE</strong>
					<p>
						At Melbourne Real Estate we know that the experience of selling property goes beyond contracts, deposits and
						commissions – it’s momentous, it’s emotional and it’s a process we’re passionate about.</p>
					<p>
						We have two teams of sales agents at MRE: our project management division, who coordinate the marketing and sales
						of newly constructed apartment complexes; and our residential sales team, who manage the sale of apartments that
						have been previously owned and/or occupied.</p>
					<p>
						Both teams are exceptionally good at converting leads into sales and will be committed to your property until it
						is sold for an exceptional price. We believe selling is a transfer of enthusiasm.</p>
					<p>
						Our track record shows we’re one of the top inner-city apartment specialists in Melbourne.</p>
					<div style="margin-top: 27px;" >
						<strong style="font-size: 21px;" >Share</strong>
						<share-card style="margin-top: 5px;" />
					</div>
				</el-card>
			</el-col>
			<el-col class="content-form" :md="24" :lg="7">
				<el-card>
					<div slot="header">
						<h3 style="margin: 0px;">Inquire about our property management service:</h3>
					</div>
					<common-form style="width: 100%;" />
				</el-card>
			</el-col>
			<el-col class="content-form" :md="24" :lg="7" style="float: right;margin-top: 30px;">
				<contacts-card :contactList="contactList" style="width: 100%;" />
			</el-col>

		</el-row>
	</div>
</template>

<script>
	import TopInfo from '@/components/TopInfo'
	import CommonForm from '@/components/CommonForm'
	import ContactsCard from '@/components/Contacts'
	import ShareCard from '@/components/ShareCard'
	export default {
		name: 'selling-page',
		components: {
			TopInfo,
			CommonForm,
			ContactsCard,
			ShareCard
		},
		data() {
			return {
				contactList: {
					'Sales': {
						email: 'info@melbournerealestate.com.au',
						direct: '+61 3 9829 2900',
						mobile: '+61 9829 2951'
					},
					'Property Management': {
						email: 'rentals@melbournerealestate.com.au',
						direct: '+61 3 9829 2900',
						mobile: '+61 9829 2966'
					}
				}
			}
		},
		created() {
			this.$nextTick(() => {
				let textHeight = this.$refs.text.offsetHeight
				let marginTop = -textHeight / 2
				Velocity(this.$refs.text, {
					marginTop: marginTop,
					top: '50%'
				}, {
					duration: 1000
				})
			})
		}
	}
</script>

<style scoped lang="scss">
	@import '@/assets/sass/mixins/responsive.scss';

	.selling {
		.content {
			margin-top: 35px;

			@include media-md {
				margin-top: 30px;
				padding: 0 30px;
			}

			@include media-sm {
				margin-top: 20px;
				padding: 0 20px;
			}

			@include media-xs {
				margin-top: 10px;
				padding: 0 10px;
			}

			&-desc {
				&-inner {
					@include media-lg-up {
						padding: 10px 10px 15px 10px;
					}

					@include media-sm-down {
						img {
							width: 100%;
						}
					}
				}

				@include media-lg-up {
					padding-right: 20px;
				}
			}

			&-form {
				@include media-md {
					margin-top: 30px;
				}

				@include media-sm {
					margin-top: 20px;
				}

				@include media-xs {
					margin-top: 10px;
				}

				p {
					font-size: 13.5px;
				}
			}
		}
	}
</style>
